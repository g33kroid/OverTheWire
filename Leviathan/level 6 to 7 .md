No Info Given

```shell
leviathan6@leviathan:~$ ls -la
total 32
drwxr-xr-x  3 leviathan6 leviathan6 4096 Oct 30 09:58 .
drwxr-xr-x 11 root       root       4096 Oct 30 09:58 ..
-rw-r--r--  1 leviathan6 leviathan6  220 Apr  9  2014 .bash_logout
-rw-r--r--  1 leviathan6 leviathan6 3637 Apr  9  2014 .bashrc
drwx------  2 leviathan6 leviathan6 4096 Oct 30 09:58 .cache
-rw-r--r--  1 leviathan6 leviathan6  675 Apr  9  2014 .profile
-r-sr-x---  1 leviathan7 leviathan6 7492 Oct 30 04:16 leviathan6
```
Lets Run the Executable 

```shell
leviathan6@leviathan:~$ ./leviathan6
usage: ./leviathan6 <4 digit code>
leviathan6@leviathan:~$ ./leviathan6 1234
Wrong
```
Lets Debug it using ltrace
```shell
leviathan6@leviathan:~$ ltrace ./leviathan6 1234
__libc_start_main(0x804850d, 2, 0xffffd7e4, 0x8048590 <unfinished ...>
atoi(0xffffd913, 0xffffd7e4, 0xffffd7f0, 0xf7e5519d)   = 1234
puts("Wrong"Wrong
)                                          = 6
+++ exited (status 6) +++

leviathan6@leviathan:~$ ltrace ./leviathan6 12345
__libc_start_main(0x804850d, 2, 0xffffd7e4, 0x8048590 <unfinished ...>
atoi(0xffffd912, 0xffffd7e4, 0xffffd7f0, 0xf7e5519d)   = 0x3039
puts("Wrong"Wrong
)                                          = 6
+++ exited (status 6) +++

leviathan6@leviathan:~$ ltrace ./leviathan6 1
__libc_start_main(0x804850d, 2, 0xffffd7e4, 0x8048590 <unfinished ...>
atoi(0xffffd916, 0xffffd7e4, 0xffffd7f0, 0xf7e5519d)   = 1
puts("Wrong"Wrong
)                                          = 6
+++ exited (status 6) +++
```
So it didn't check if i input 4 digit code or not 

Lets do full reverse 

```python
def main(argc, argv):
    # 0x804850d
    if argc != 2:
        # 0x8048524
        printf("usage: %s <4 digit code>\n", *argv)
        exit(-1)
        # UNREACHABLE
    if atoi(argv[4]) == 0x1bd3:
        # 0x804855b
        seteuid(1007)
        system_rc = system("/bin/sh")
        # branch -> 0x8048581
    else:
        # 0x8048575
        system_rc = puts("Wrong")
        # branch -> 0x8048581
    # 0x8048581
    return system_rc
```
So its looking for argv[4] to be 7132 a specific thing otherwise print wrong 
**HINT** Brute force the service 

So I wrote bash script to brute force the executable 

```shell
leviathan6@leviathan:~$ mkdir /tmp/menz
leviathan6@leviathan:~$ cp leviathan6 /tmp/menz
leviathan6@leviathan:~$ cd /tmp/menz/
leviathan6@leviathan:/tmp/menz$ nano cracker.sh
leviathan6@leviathan:/tmp/menz$ cat cracker.sh
#!/bin/bash

for i in {0000..9999}
do
echo "Testing Pin $i"
./leviathan6 $i
done

```
Lets give it executable permission and run it 

```shell
leviathan6@leviathan:/tmp/menz$ chmod +x cracker.sh
```
running the script below is snippet of the output

```shell
Testing Pin 7121
Wrong
Testing Pin 7122
Wrong
Testing Pin 7123
$
```
We Got a Shell
```shell
$ whoami
leviathan6
```
Now this issue because i copied the file to /tmp/ so lets edit the script to use the original file 

```shell
leviathan6@leviathan:/tmp/menz$ cat cracker.sh
#!/bin/bash

for i in {0000..9999}
do
echo "Testing Pin $i"
~/leviathan6 $i
done
```
Run it agian Or just simply take the 4digit code that was found and run the executable in original directory it will have same effect
```shell
Testing Pin 7122
Wrong
Testing Pin 7123
$ whoami
leviathan7
```
and here is our flag
```shell
$ cat /etc/leviathan_pass/leviathan7
ahy7MaeBo9
```
