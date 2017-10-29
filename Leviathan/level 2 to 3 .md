No Info Given 

```shell
leviathan2@leviathan:~$ ls -la
total 32
drwxr-xr-x  3 leviathan2 leviathan2 4096 Oct 29 12:16 .
drwxr-xr-x 11 root       root       4096 Oct 29 12:16 ..
-rw-r--r--  1 leviathan2 leviathan2  220 Apr  9  2014 .bash_logout
-rw-r--r--  1 leviathan2 leviathan2 3637 Apr  9  2014 .bashrc
drwx------  2 leviathan2 leviathan2 4096 Oct 29 12:16 .cache
-rw-r--r--  1 leviathan2 leviathan2  675 Apr  9  2014 .profile
-r-sr-x---  1 leviathan3 leviathan2 7506 Oct 23 04:20 printfile
```
Lets Run printfile

```shell
leviathan2@leviathan:~$ ./printfile
*** File Printer ***
Usage: ./printfile filename
leviathan2@leviathan:~$ ./printfile /etc/leviathan_pass/leviathan3
You cant have that file...
```
Time to reverse this thing to its original code 

```python
def main(argc, argv):
    v1 = *20 # 0x8048541
    if argc <= 1:
        # 0x8048555
        puts("*** File Printer ***")
        printf("Usage: %s filename\n", *argv)
        # branch -> 0x80485e8
        # 0x80485e8
        if *20 != v1:
            # 0x80485f8
            __stack_chk_fail()
            # branch -> 0x80485fd
        # 0x80485fd
        return -1
    path = argv + 4 # 0x8048585_0
    if access(*path, R_OK) == 0:
        snprintf(&str, 511, "/bin/cat %s", *path)
        system(&str)
        result = 0
        # branch -> 0x80485e8
    else:
        # 0x804859b
        puts("You cant have that file...")
        result = 1
        # branch -> 0x80485e8
    # 0x80485e8
    if *20 != v1:
        # 0x80485f8
        __stack_chk_fail()
        # branch -> 0x80485fd
    # 0x80485fd
    return result
```

The Above code we give it a path and the issue we can't read the file , Permission Denied so we need to find a way around it 

Testing the file with ltrace

```shell
leviathan2@leviathan:~$ ltrace ./printfile /etc/leviathan_pass/leviathan2
__libc_start_main(0x804852d, 2, 0xffffd7c4, 0x8048600 <unfinished ...>
access("/etc/leviathan_pass/leviathan2", 4)                  = 0
snprintf("/bin/cat /etc/leviathan_pass/lev"..., 511, "/bin/cat %s", "/etc/leviathan_pass/leviathan2") = 39
system("/bin/cat /etc/leviathan_pass/lev"...ougahZi8Ta
 <no return ...>
--- SIGCHLD (Child exited) ---
<... system resumed> )                                       = 0
+++ exited (status 0) +++
```
so what happen is access do permission check if we have access to read the file or not
and what cat do is do it don't need the full path for the file 
so if we created a symbolic link between tmp.txt and /etc/leviathan_pass/leviathan3 
we can get both rules correct at same time



