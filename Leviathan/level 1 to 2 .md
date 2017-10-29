No Info were given 

lets connect and see what we have 

```shell
leviathan1@leviathan:~$ ls -la
total 32
drwxr-xr-x  3 leviathan1 leviathan1 4096 Oct 29 11:04 .
drwxr-xr-x 11 root       root       4096 Oct 29 11:04 ..
-rw-r--r--  1 leviathan1 leviathan1  220 Apr  9  2014 .bash_logout
-rw-r--r--  1 leviathan1 leviathan1 3637 Apr  9  2014 .bashrc
drwx------  2 leviathan1 leviathan1 4096 Oct 29 11:04 .cache
-rw-r--r--  1 leviathan1 leviathan1  675 Apr  9  2014 .profile
-r-sr-x---  1 leviathan2 leviathan1 7501 Oct 23 04:20 check
```
Running **check** file 

```shell
leviathan1@leviathan:~$ ./check
password: 123
Wrong password, Good Bye ...
```

Lets see what file is that 

```shell
leviathan1@leviathan:~$ file check
check: setuid ELF 32-bit LSB  executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.24, BuildID[sha1]=4c5a895c73faa38da165925e8c0deeded68f5c1d, not stripped
```
After Decompiling the code using https://retdec.com

```c
// Address range: 0x804852d - 0x80485ef
int main(int argc, char ** argv) {
    char v1; // 0x804a034
    int32_t str2 = 0x786573; // bp-40
    printf("password: ");
    int32_t str = 0x1000000 * getchar() / 0x1000000; // bp-44
    getchar();
    getchar();
    if (strcmp((char *)&str, (char *)&str2) == 0) {
        // 0x80485b7
        system("/bin/sh");
        // branch -> 0x80485d1
    } else {
        // 0x80485c5
        puts("Wrong password, Good Bye ...");
        // branch -> 0x80485d1
    }
    // 0x80485d1
    int32_t v2; // 0x8048537
    int32_t v3; // 0x80485db
    if (v3 != v2) {
        // 0x80485e3
        __stack_chk_fail();
        // branch -> 0x80485e8
    }
    // 0x80485e8
    return 0;
}
```
or the same code in python 

```python
When i Enter 0 or 1 or any other 1 digit char it stop and ask for more char whatever comes next says wrong password
Need to test it 

okay forget about the above code :D its good to learn new tools 

They key to solve this is by using **ltrace**

lets run the ./check using ltrace and see the output 
```shell
leviathan1@leviathan:~$ ltrace ./check
__libc_start_main(0x804852d, 1, 0xffffd804, 0x80485f0 <unfinished ...>
printf("password: ")                                         = 10
getchar(0x8048680, 47, 0x804a000, 0x8048642password: something_here
)                 = 115
getchar(0x8048680, 47, 0x804a000, 0x8048642)                 = 111
getchar(0x8048680, 47, 0x804a000, 0x8048642)                 = 109
strcmp("som", "sex")                                         = 1
puts("Wrong password, Good Bye ..."Wrong password, Good Bye ...
)                         = 29
+++ exited (status 0) +++
```
we see we have entered *something_here and it compare it with word *sex*

so lets run it again and use the password *sex*

```shell
leviathan1@leviathan:~$ ./check sex
password: sex
$ whoami
leviathan2
$ cat /etc/leviathan_pass/leviathan2
ougahZi8Ta
```



