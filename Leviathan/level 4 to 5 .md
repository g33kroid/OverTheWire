No Information given

```shell
leviathan4@leviathan:~$ ls -la
total 28
drwxr-xr-x  4 leviathan4 leviathan4 4096 Oct 30 09:10 .
drwxr-xr-x 11 root       root       4096 Oct 30 09:10 ..
-rw-r--r--  1 leviathan4 leviathan4  220 Apr  9  2014 .bash_logout
-rw-r--r--  1 leviathan4 leviathan4 3637 Apr  9  2014 .bashrc
drwx------  2 leviathan4 leviathan4 4096 Oct 30 09:10 .cache
-rw-r--r--  1 leviathan4 leviathan4  675 Apr  9  2014 .profile
dr-xr-x---  2 root       leviathan4 4096 Oct 30 04:16 .trash
```
So this time there are no executables but there is .trash 
lets explore it
```shell
leviathan4@leviathan:~$ cd .trash/
leviathan4@leviathan:~/.trash$ ls -la
total 16
dr-xr-x--- 2 root       leviathan4 4096 Oct 30 04:16 .
drwxr-xr-x 4 leviathan4 leviathan4 4096 Oct 30 09:10 ..
-r-sr-x--- 1 leviathan5 leviathan4 7433 Oct 30 04:16 bin
leviathan4@leviathan:~/.trash$ file bin
bin: setuid ELF 32-bit LSB  executable, Intel 80386, version 1 (SYSV),
dynamically linked (uses shared libs),
for GNU/Linux 2.6.24, BuildID[sha1]=58046a7bfbedab2f6a7d5c8e9a97f32c3358e7e7, not stripped
```
Found an executable lets give it a shot 
```shell
leviathan4@leviathan:~/.trash$ ./bin
01010100 01101001 01110100 01101000 00110100 01100011 01101111 01101011 01100101 01101001 00001010
```
lets try to convert these binaries 

Converting the binary showed this word : Tith4cokei

so lets see what happen inside ltrace to make sure its our password 
```shell
leviathan4@leviathan:~/.trash$ ltrace ./bin
__libc_start_main(0x80484cd, 1, 0xffffd7d4, 0x80485c0 <unfinished ...>
fopen("/etc/leviathan_pass/leviathan5", "r")                   = 0
+++ exited (status 255) +++
```
yeah its our password 
