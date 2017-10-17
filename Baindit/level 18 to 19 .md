The password for the next level is stored in a file readme in the homedirectory. Unfortunately,
someone has modified .bashrc to log you out when you log in with SSH.

using this password from previous level **kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd** 

Note we have added **/bin/sh** to avoid **bye Bye in output**

```shell
bandit17@bandit:~$ ssh bandit18@localhost -p 2220 /bin/sh
The authenticity of host '[localhost]:2220 ([127.0.0.1]:2220)' can't be established.
ECDSA key fingerprint is ee:4c:8c:e7:57:2c:bc:63:24:b8:e6:23:27:63:72:9f.
Are you sure you want to continue connecting (yes/no)? yes
Failed to add the host to the list of known hosts (/home/bandit17/.ssh/known_hosts).
 _                     _ _ _   
| |__   __ _ _ __   __| (_) |_ 
| '_ \ / _` | '_ \ / _` | | __|
| |_) | (_| | | | | (_| | | |_ 
|_.__/ \__,_|_| |_|\__,_|_|\__|
                               
a http://www.overthewire.org wargame.

@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@         WARNING: UNPROTECTED PRIVATE KEY FILE!          @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
Permissions 0640 for '/home/bandit17/.ssh/id_rsa' are too open.
It is required that your private key files are NOT accessible by others.
This private key will be ignored.
bad permissions: ignore key: /home/bandit17/.ssh/id_rsa
bandit18@localhost's password: 
id
uid=11018(bandit18) gid=11018(bandit18) groups=11018(bandit18)
ls -la
total 28
drwxr-xr-x  3 bandit18 bandit18 4096 Oct 17 20:21 .
drwxr-xr-x 32 root     root     4096 Oct 17 20:21 ..
-rw-r--r--  1 bandit18 bandit18  220 Apr  9  2014 .bash_logout
-rw-r-----  1 bandit19 bandit18 3660 Sep 28 14:04 .bashrc
drwx------  2 bandit18 bandit18 4096 Oct 17 20:21 .cache
-rw-r--r--  1 bandit18 bandit18  675 Apr  9  2014 .profile
-rw-r-----  1 bandit19 bandit18   33 Sep 28 14:04 readme
cat readme	
IueksS7Ubh8G3DCwVzrTd8rAVOwq3M5x
```
