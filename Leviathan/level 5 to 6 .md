No info given 

```shell
leviathan5@leviathan:~$ ls -la
total 32
drwxr-xr-x  3 leviathan5 leviathan5 4096 Oct 30 09:17 .
drwxr-xr-x 11 root       root       4096 Oct 30 09:17 ..
-rw-r--r--  1 leviathan5 leviathan5  220 Apr  9  2014 .bash_logout
-rw-r--r--  1 leviathan5 leviathan5 3637 Apr  9  2014 .bashrc
drwx------  2 leviathan5 leviathan5 4096 Oct 30 09:17 .cache
-rw-r--r--  1 leviathan5 leviathan5  675 Apr  9  2014 .profile
-r-sr-x---  1 leviathan6 leviathan5 7642 Oct 30 04:16 leviathan5
```
Lets Run the executable see what it is doing
```shell
leviathan5@leviathan:~$ ./leviathan5
Cannot find /tmp/file.log
```
Lets create /tmp/file.log
```shell
leviathan5@leviathan:~$ touch /tmp/file.log
leviathan5@leviathan:~$ ./leviathan5
leviathan5@leviathan:~$ cat /tmp/file.log
cat: /tmp/file.log: No such file or directory
```
so I assume that it removes the file or rename it lets look at ltrace
```shell
leviathan5@leviathan:~$ ltrace ./leviathan5
__libc_start_main(0x80485ed, 1, 0xffffd7f4, 0x8048690 <unfinished ...>
fopen("/tmp/file.log", "r")                   = 0
puts("Cannot find /tmp/file.log"Cannot find /tmp/file.log
)             = 26
exit(-1 <no return ...>
+++ exited (status 255) +++
```
Lets recreate tmp/file.log and see what happen with ltrace

```shell
leviathan5@leviathan:~$ touch /tmp/file.log
leviathan5@leviathan:~$ ltrace ./leviathan5
__libc_start_main(0x80485ed, 1, 0xffffd7f4, 0x8048690 <unfinished ...>
fopen("/tmp/file.log", "r")                   = 0x804b008
fgetc(0x804b008)                              = '\377'
feof(0x804b008)                               = 1
fclose(0x804b008)                             = 0
getuid()                                      = 12005
setuid(12005)                                 = 0
unlink("/tmp/file.log")                       = 0
+++ exited (status 0) +++
I dont fully understand the code lets do full reverse 

So it opened file.log for read 
get 1 character 
check if its end of file 
close the file 
get the id of user in this case 12005 which is leviathan5 
set id of the user who calls the process in this case leviathan5
remove the file symbolic link 

what if the file contain characters instead of being empty 

so i was correct something has changed in ltrace output lets see what happen 
I have created file.log and added the character 'x' saved in /tmp/file.log

```shell
leviathan5@leviathan:~$ ltrace ./leviathan5
__libc_start_main(0x80485ed, 1, 0xffffd7f4, 0x8048690 <unfinished ...>
fopen("/tmp/file.log", "r")            = 0x804b008
fgetc(0x804b008)                       = 'x'
feof(0x804b008)                        = 0
putchar(120, 0x8048720, 0xffffd7fc, 0xf7e5519d) = 120
fgetc(0x804b008)                       = '\n'
feof(0x804b008)                        = 0
putchar(10, 0x8048720, 0xffffd7fc, 0xf7e5519dx
) = 10
fgetc(0x804b008)                       = '\377'
feof(0x804b008)                        = 1
fclose(0x804b008)                      = 0
getuid()                               = 12005
setuid(12005)                          = 0
unlink("/tmp/file.log")                = 0
+++ exited (status 0) +++
```
so it wrote back the character x and unlink the file 
```shell
leviathan5@leviathan:~$ ./leviathan5
x
```

a full code is here 
```python
def main(argc, argv):
    file = fopen("/tmp/file.log", "r") # 0x8048605
    if file == NULL:
        # 0x8048615
        puts("Cannot find /tmp/file.log")
        exit(-1)
        # UNREACHABLE
    c = fgetc(file) # 0x80486346
    if feof(file) != 0:
        # 0x804865e
        fclose(file)
        uid = getuid()
        setuid(uid)
        unlink("/tmp/file.log")
        return 0
    putchar(0x1000000 * c / 0x1000000)
    c2 = fgetc(file) # 0x8048634
    while feof(file) == 0:
        # 0x804864f
        putchar(0x1000000 * c2 / 0x1000000)
        c2 = fgetc(file)
        # continue -> 0x804864f
    # 0x804865e
    fclose(file)
    uid = getuid()
    setuid(uid)
    unlink("/tmp/file.log")
    return 0
```
so what ever is in the file it output it as it is till end of file reached then it unlink the file 
```shell
 ./leviathan5
cat /etc/leviathan_pass/leviathan6
```
lets try again with ltrace

```shell
leviathan5@leviathan:~$ ltrace ./leviathan5
__libc_start_main(0x80485ed, 1, 0xffffd7f4, 0x8048690 <unfinished ...>
fopen("/tmp/file.log", "r")            = 0x804b008
fgetc(0x804b008)                       = 'c'
feof(0x804b008)                        = 0
putchar(99, 0x8048720, 0xffffd7fc, 0xf7e5519d) = 99
fgetc(0x804b008)                       = 'a'
feof(0x804b008)                        = 0
putchar(97, 0x8048720, 0xffffd7fc, 0xf7e5519d) = 97
fgetc(0x804b008)                       = 't'
feof(0x804b008)                        = 0
putchar(116, 0x8048720, 0xffffd7fc, 0xf7e5519d) = 116
fgetc(0x804b008)                       = ' '
feof(0x804b008)                        = 0
putchar(32, 0x8048720, 0xffffd7fc, 0xf7e5519d) = 32
fgetc(0x804b008)                       = '/'
feof(0x804b008)                        = 0
putchar(47, 0x8048720, 0xffffd7fc, 0xf7e5519d) = 47
fgetc(0x804b008)                       = 'e'
feof(0x804b008)                        = 0
putchar(101, 0x8048720, 0xffffd7fc, 0xf7e5519d) = 101
fgetc(0x804b008)                       = 't'
feof(0x804b008)                        = 0
putchar(116, 0x8048720, 0xffffd7fc, 0xf7e5519d) = 116
fgetc(0x804b008)                       = 'c'
feof(0x804b008)                        = 0
putchar(99, 0x8048720, 0xffffd7fc, 0xf7e5519d) = 99
fgetc(0x804b008)                       = '/'
feof(0x804b008)                        = 0
putchar(47, 0x8048720, 0xffffd7fc, 0xf7e5519d) = 47
fgetc(0x804b008)                       = 'l'
feof(0x804b008)                        = 0
putchar(108, 0x8048720, 0xffffd7fc, 0xf7e5519d) = 108
fgetc(0x804b008)                       = 'e'
feof(0x804b008)                        = 0
putchar(101, 0x8048720, 0xffffd7fc, 0xf7e5519d) = 101
fgetc(0x804b008)                       = 'v'
feof(0x804b008)                        = 0
putchar(118, 0x8048720, 0xffffd7fc, 0xf7e5519d) = 118
fgetc(0x804b008)                       = 'i'
feof(0x804b008)                        = 0
putchar(105, 0x8048720, 0xffffd7fc, 0xf7e5519d) = 105
fgetc(0x804b008)                       = 'a'
feof(0x804b008)                        = 0
putchar(97, 0x8048720, 0xffffd7fc, 0xf7e5519d) = 97
fgetc(0x804b008)                       = 't'
feof(0x804b008)                        = 0
putchar(116, 0x8048720, 0xffffd7fc, 0xf7e5519d) = 116
fgetc(0x804b008)                       = 'h'
feof(0x804b008)                        = 0
putchar(104, 0x8048720, 0xffffd7fc, 0xf7e5519d) = 104
fgetc(0x804b008)                       = 'a'
feof(0x804b008)                        = 0
putchar(97, 0x8048720, 0xffffd7fc, 0xf7e5519d) = 97
fgetc(0x804b008)                       = 'n'
feof(0x804b008)                        = 0
putchar(110, 0x8048720, 0xffffd7fc, 0xf7e5519d) = 110
fgetc(0x804b008)                       = '_'
feof(0x804b008)                        = 0
putchar(95, 0x8048720, 0xffffd7fc, 0xf7e5519d) = 95
fgetc(0x804b008)                       = 'p'
feof(0x804b008)                        = 0
putchar(112, 0x8048720, 0xffffd7fc, 0xf7e5519d) = 112
fgetc(0x804b008)                       = 'a'
feof(0x804b008)                        = 0
putchar(97, 0x8048720, 0xffffd7fc, 0xf7e5519d) = 97
fgetc(0x804b008)                       = 's'
feof(0x804b008)                        = 0
putchar(115, 0x8048720, 0xffffd7fc, 0xf7e5519d) = 115
fgetc(0x804b008)                       = 's'
feof(0x804b008)                        = 0
putchar(115, 0x8048720, 0xffffd7fc, 0xf7e5519d) = 115
fgetc(0x804b008)                       = '/'
feof(0x804b008)                        = 0
putchar(47, 0x8048720, 0xffffd7fc, 0xf7e5519d) = 47
fgetc(0x804b008)                       = 'l'
feof(0x804b008)                        = 0
putchar(108, 0x8048720, 0xffffd7fc, 0xf7e5519d) = 108
fgetc(0x804b008)                       = 'e'
feof(0x804b008)                        = 0
putchar(101, 0x8048720, 0xffffd7fc, 0xf7e5519d) = 101
fgetc(0x804b008)                       = 'v'
feof(0x804b008)                        = 0
putchar(118, 0x8048720, 0xffffd7fc, 0xf7e5519d) = 118
fgetc(0x804b008)                       = 'i'
feof(0x804b008)                        = 0
putchar(105, 0x8048720, 0xffffd7fc, 0xf7e5519d) = 105
fgetc(0x804b008)                       = 'a'
feof(0x804b008)                        = 0
putchar(97, 0x8048720, 0xffffd7fc, 0xf7e5519d) = 97
fgetc(0x804b008)                       = 't'
feof(0x804b008)                        = 0
putchar(116, 0x8048720, 0xffffd7fc, 0xf7e5519d) = 116
fgetc(0x804b008)                       = 'h'
feof(0x804b008)                        = 0
putchar(104, 0x8048720, 0xffffd7fc, 0xf7e5519d) = 104
fgetc(0x804b008)                       = 'a'
feof(0x804b008)                        = 0
putchar(97, 0x8048720, 0xffffd7fc, 0xf7e5519d) = 97
fgetc(0x804b008)                       = 'n'
feof(0x804b008)                        = 0
putchar(110, 0x8048720, 0xffffd7fc, 0xf7e5519d) = 110
fgetc(0x804b008)                       = '6'
feof(0x804b008)                        = 0
putchar(54, 0x8048720, 0xffffd7fc, 0xf7e5519d) = 54
fgetc(0x804b008)                       = '\n'
feof(0x804b008)                        = 0
putchar(10, 0x8048720, 0xffffd7fc, 0xf7e5519dcat /etc/leviathan_pass/leviathan6
) = 10
fgetc(0x804b008)                       = '\377'
feof(0x804b008)                        = 1
fclose(0x804b008)                      = 0
getuid()                               = 12005
setuid(12005)                          = 0
unlink("/tmp/file.log")                = 0
```
so we can do a symbolic link between /tmp/file.log and leviathan6 password lets give that a shot 

```shell
leviathan5@leviathan:~$ ln -s /etc/leviathan_pass/leviathan6 /tmp/file.log
leviathan5@leviathan:~$ ./leviathan5
UgaoFee4li
```
Bingooooooooooooooooo
