No information were given so lets see what can we find 

```shell
leviathan0@leviathan:~$ ls -la
total 28
drwxr-xr-x  4 leviathan0 leviathan0 4096 Oct 29 08:37 .
drwxr-xr-x 11 root       root       4096 Oct 29 08:37 ..
drwxr-x---  2 leviathan1 leviathan0 4096 Oct 23 04:20 .backup
-rw-r--r--  1 leviathan0 leviathan0  220 Apr  9  2014 .bash_logout
-rw-r--r--  1 leviathan0 leviathan0 3637 Apr  9  2014 .bashrc
drwx------  2 leviathan0 leviathan0 4096 Oct 29 08:37 .cache
-rw-r--r--  1 leviathan0 leviathan0  675 Apr  9  2014 .profile
leviathan0@leviathan:~$ ls -la /etc/leviathan_pass/
total 40
drwxr-xr-x   2 root       root       4096 Oct 23 04:20 .
drwxr-xr-x 114 root       root       4096 Oct 29 08:37 ..
-r--------   1 leviathan0 leviathan0   11 Oct 23 04:20 leviathan0
-r--------   1 leviathan1 leviathan1   11 Oct 23 04:20 leviathan1
-r--------   1 leviathan2 leviathan2   11 Oct 23 04:20 leviathan2
-r--------   1 leviathan3 leviathan3   11 Oct 23 04:20 leviathan3
-r--------   1 leviathan4 leviathan4   11 Oct 23 04:20 leviathan4
-r--------   1 leviathan5 leviathan5   11 Oct 23 04:20 leviathan5
-r--------   1 leviathan6 leviathan6   11 Oct 23 04:20 leviathan6
-r--------   1 leviathan7 leviathan7   11 Oct 23 04:20 leviathan7
leviathan0@leviathan:~$ cat /etc/leviathan_pass/leviathan0
leviathan0
leviathan0@leviathan:~$ cat /etc/leviathan_pass/leviathan1
cat: /etc/leviathan_pass/leviathan1: Permission denied
```
okay so nothing here seems useful

Quick nmap scan

```shell
leviathan0@leviathan:~$ nmap localhost

Starting Nmap 6.40 ( http://nmap.org ) at 2017-10-29 08:40 UTC
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00048s latency).
Other addresses for localhost (not scanned): 127.0.0.1
Not shown: 998 closed ports
PORT    STATE SERVICE
22/tcp  open  ssh
113/tcp open  ident

Nmap done: 1 IP address (1 host up) scanned in 0.06 seconds
```
In Description says : Data for the levels can be found in the homedirectories.

so lets check each file/folder in home directory 
```shell
leviathan0@leviathan:~$ cd .backup/
leviathan0@leviathan:~/.backup$ ls -la
total 140
drwxr-x--- 2 leviathan1 leviathan0   4096 Oct 23 04:20 .
drwxr-xr-x 4 leviathan0 leviathan0   4096 Oct 29 08:40 ..
-rw-r----- 1 leviathan1 leviathan0 133259 Oct 23 04:20 bookmarks.html
```
reading bookmarks.html give me huge html page so lets try to filter for password

Password is here 
```shell
leviathan0@leviathan:~/.backup$ cat bookmarks.html | grep password
<DT><A HREF="http://leviathan.labs.overthewire.org/passwordus.html | This will be fixed later, the password for leviathan1 is rioGegei8m" ADD_DATE="1155384634" LAST_CHARSET="ISO-8859-1" ID="rdf:#$2wIU71">password to leviathan1</A>
```
Leviathan1 Pass : rioGegei8m
