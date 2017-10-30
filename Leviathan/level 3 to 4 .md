No Information Given

```shell
leviathan3@leviathan:~$ ls -la
total 36
drwxr-xr-x  3 leviathan3 leviathan3 4096 Oct 30 08:55 .
drwxr-xr-x 11 root       root       4096 Oct 30 08:55 ..
-rw-r--r--  1 leviathan3 leviathan3  220 Apr  9  2014 .bash_logout
-rw-r--r--  1 leviathan3 leviathan3 3637 Apr  9  2014 .bashrc
drwx------  2 leviathan3 leviathan3 4096 Oct 30 08:55 .cache
-rw-r--r--  1 leviathan3 leviathan3  675 Apr  9  2014 .profile
-r-sr-x---  1 leviathan4 leviathan3 9946 Oct 30 04:16 level3
```
Lets Execute level3

```shell
leviathan3@leviathan:~$ ./level3
Enter the password> something
bzzzzzzzzap. WRONG
```

Lets Check what happen inside ltrace

```shell
leviathan3@leviathan:~$ ltrace ./level3
__libc_start_main(0x80485fe, 1, 0xffffd804, 0x80486d0 <unfinished ...>
strcmp("h0no33", "kakaka")               = -1
printf("Enter the password> ")           = 20
fgets(Enter the password> something
"something\n", 256, 0xf7fccc20)    = 0xffffd5fc
strcmp("something\n", "snlprintf\n")     = 1
puts("bzzzzzzzzap. WRONG"bzzzzzzzzap. WRONG
)               = 19
+++ exited (status 0) +++
```
so it compares **something** what we input to **snlprintf**

Now lets use **snlprintf**

```shell
leviathan3@leviathan:~$ ltrace ./level3
__libc_start_main(0x80485fe, 1, 0xffffd804, 0x80486d0 <unfinished ...>
strcmp("h0no33", "kakaka")               = -1
printf("Enter the password> ")           = 20
fgets(Enter the password> snlprintf
"snlprintf\n", 256, 0xf7fccc20)    = 0xffffd5fc
strcmp("snlprintf\n", "snlprintf\n")     = 0
puts("[You've got shell]!"[You've got shell]!
)              = 20
system("/bin/sh"$ whoami
leviathan3
``` 
Lets Try without ltrace 

```shell
leviathan3@leviathan:~$ ./level3
Enter the password> snlprintf
[You've got shell]!
$ whoami
leviathan4
$ cat /etc/leviathan_pass/leviathan4
vuH0coox6m
```

