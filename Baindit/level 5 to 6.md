The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:

   **human-readable**
   **1033 bytes in size**
   **not executable**

```shell
┌─[✗]─[microbot@parrot]─[~]
└──╼ $sudo ssh  bandit5@bandit.labs.overthewire.org -p 2220
 _                     _ _ _   
| |__   __ _ _ __   __| (_) |_ 
| '_ \ / _` | '_ \ / _` | | __|
| |_) | (_| | | | | (_| | | |_ 
|_.__/ \__,_|_| |_|\__,_|_|\__|
                               
a http://www.overthewire.org wargame.

bandit5@bandit.labs.overthewire.org's password: 
Welcome to Ubuntu 14.04 LTS (GNU/Linux 4.4.0-92-generic x86_64)

 * Documentation:  https://help.ubuntu.com/

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

bandit5@bandit:~$ ls
inhere
bandit5@bandit:~$ ls -la
total 28
drwxr-xr-x  4 bandit5 bandit5 4096 Oct  2 20:12 .
drwxr-xr-x 30 root    root    4096 Oct  2 20:12 ..
-rw-r--r--  1 bandit5 bandit5  220 Apr  9  2014 .bash_logout
-rw-r--r--  1 bandit5 bandit5 3637 Apr  9  2014 .bashrc
drwx------  2 bandit5 bandit5 4096 Oct  2 20:12 .cache
-rw-r--r--  1 bandit5 bandit5  675 Apr  9  2014 .profile
drwxr-x--- 22 root    bandit5 4096 Sep 28 14:04 inhere
bandit5@bandit:~$ cd inhere/
bandit5@bandit:~/inhere$ ls -la
total 88
drwxr-x--- 22 root    bandit5 4096 Sep 28 14:04 .
drwxr-xr-x  4 bandit5 bandit5 4096 Oct  2 20:12 ..
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere00
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere01
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere02
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere03
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere04
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere05
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere06
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere07
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere08
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere09
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere10
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere11
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere12
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere13
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere14
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere15
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere16
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere17
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere18
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere19
bandit5@bandit:~/inhere$ cd ..  
bandit5@bandit:~$ ls -alR inhere/
inhere/:
total 88
drwxr-x--- 22 root    bandit5 4096 Sep 28 14:04 .
drwxr-xr-x  4 bandit5 bandit5 4096 Oct  2 20:12 ..
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere00
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere01
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere02
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere03
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere04
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere05
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere06
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere07
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere08
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere09
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere10
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere11
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere12
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere13
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere14
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere15
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere16
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere17
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere18
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere19

inhere/maybehere00:
total 72
-rwxr-x---  1 root bandit5 1039 Sep 28 14:04 -file1
-rw-r-----  1 root bandit5 9388 Sep 28 14:04 -file2
-rwxr-x---  1 root bandit5 7378 Sep 28 14:04 -file3
drwxr-x---  2 root bandit5 4096 Sep 28 14:04 .
drwxr-x--- 22 root bandit5 4096 Sep 28 14:04 ..
-rwxr-x---  1 root bandit5  551 Sep 28 14:04 .file1
-rw-r-----  1 root bandit5 7836 Sep 28 14:04 .file2
-rwxr-x---  1 root bandit5 4802 Sep 28 14:04 .file3
-rwxr-x---  1 root bandit5 6118 Sep 28 14:04 spaces file1
-rw-r-----  1 root bandit5 6850 Sep 28 14:04 spaces file2
-rwxr-x---  1 root bandit5 1915 Sep 28 14:04 spaces file3

inhere/maybehere01:
total 80
-rwxr-x---  1 root bandit5 6028 Sep 28 14:04 -file1
-rw-r-----  1 root bandit5  288 Sep 28 14:04 -file2
-rwxr-x---  1 root bandit5 9641 Sep 28 14:04 -file3
drwxr-x---  2 root bandit5 4096 Sep 28 14:04 .
drwxr-x--- 22 root bandit5 4096 Sep 28 14:04 ..
-rwxr-x---  1 root bandit5 8944 Sep 28 14:04 .file1
-rw-r-----  1 root bandit5 3070 Sep 28 14:04 .file2
-rwxr-x---  1 root bandit5 3792 Sep 28 14:04 .file3
-rwxr-x---  1 root bandit5 4139 Sep 28 14:04 spaces file1
-rw-r-----  1 root bandit5 4543 Sep 28 14:04 spaces file2
-rwxr-x---  1 root bandit5 8834 Sep 28 14:04 spaces file3

inhere/maybehere02:
total 68
-rwxr-x---  1 root bandit5 3801 Sep 28 14:04 -file1
-rw-r-----  1 root bandit5 3511 Sep 28 14:04 -file2
-rwxr-x---  1 root bandit5 4932 Sep 28 14:04 -file3
drwxr-x---  2 root bandit5 4096 Sep 28 14:04 .
drwxr-x--- 22 root bandit5 4096 Sep 28 14:04 ..
-rwxr-x---  1 root bandit5 6351 Sep 28 14:04 .file1
-rw-r-----  1 root bandit5 2577 Sep 28 14:04 .file2
-rwxr-x---  1 root bandit5 7953 Sep 28 14:04 .file3
-rwxr-x---  1 root bandit5 6746 Sep 28 14:04 spaces file1
-rw-r-----  1 root bandit5 8488 Sep 28 14:04 spaces file2
-rwxr-x---  1 root bandit5 2275 Sep 28 14:04 spaces file3

inhere/maybehere03:
total 80
-rwxr-x---  1 root bandit5  315 Sep 28 14:04 -file1
-rw-r-----  1 root bandit5 6595 Sep 28 14:04 -file2
-rwxr-x---  1 root bandit5 8275 Sep 28 14:04 -file3
drwxr-x---  2 root bandit5 4096 Sep 28 14:04 .
drwxr-x--- 22 root bandit5 4096 Sep 28 14:04 ..
-rwxr-x---  1 root bandit5 9769 Sep 28 14:04 .file1
-rw-r-----  1 root bandit5 8880 Sep 28 14:04 .file2
-rwxr-x---  1 root bandit5 2282 Sep 28 14:04 .file3
-rwxr-x---  1 root bandit5 2190 Sep 28 14:04 spaces file1
-rw-r-----  1 root bandit5 3385 Sep 28 14:04 spaces file2
-rwxr-x---  1 root bandit5 9234 Sep 28 14:04 spaces file3

inhere/maybehere04:
total 60
-rwxr-x---  1 root bandit5 4410 Sep 28 14:04 -file1
-rw-r-----  1 root bandit5 2619 Sep 28 14:04 -file2
-rwxr-x---  1 root bandit5 2117 Sep 28 14:04 -file3
drwxr-x---  2 root bandit5 4096 Sep 28 14:04 .
drwxr-x--- 22 root bandit5 4096 Sep 28 14:04 ..
-rwxr-x---  1 root bandit5 2440 Sep 28 14:04 .file1
-rw-r-----  1 root bandit5 6144 Sep 28 14:04 .file2
-rwxr-x---  1 root bandit5  142 Sep 28 14:04 .file3
-rwxr-x---  1 root bandit5 5532 Sep 28 14:04 spaces file1
-rw-r-----  1 root bandit5 2491 Sep 28 14:04 spaces file2
-rwxr-x---  1 root bandit5 6002 Sep 28 14:04 spaces file3

inhere/maybehere05:
total 64
-rwxr-x---  1 root bandit5 2346 Sep 28 14:04 -file1
-rw-r-----  1 root bandit5 5959 Sep 28 14:04 -file2
-rwxr-x---  1 root bandit5 2572 Sep 28 14:04 -file3
drwxr-x---  2 root bandit5 4096 Sep 28 14:04 .
drwxr-x--- 22 root bandit5 4096 Sep 28 14:04 ..
-rwxr-x---  1 root bandit5 3201 Sep 28 14:04 .file1
-rw-r-----  1 root bandit5 5917 Sep 28 14:04 .file2
-rwxr-x---  1 root bandit5 4585 Sep 28 14:04 .file3
-rwxr-x---  1 root bandit5  880 Sep 28 14:04 spaces file1
-rw-r-----  1 root bandit5 2420 Sep 28 14:04 spaces file2
-rwxr-x---  1 root bandit5 8585 Sep 28 14:04 spaces file3

inhere/maybehere06:
total 64
-rwxr-x---  1 root bandit5 5731 Sep 28 14:04 -file1
-rw-r-----  1 root bandit5 1076 Sep 28 14:04 -file2
-rwxr-x---  1 root bandit5 3443 Sep 28 14:04 -file3
drwxr-x---  2 root bandit5 4096 Sep 28 14:04 .
drwxr-x--- 22 root bandit5 4096 Sep 28 14:04 ..
-rwxr-x---  1 root bandit5 1271 Sep 28 14:04 .file1
-rw-r-----  1 root bandit5 8976 Sep 28 14:04 .file2
-rwxr-x---  1 root bandit5 2418 Sep 28 14:04 .file3
-rwxr-x---  1 root bandit5 4073 Sep 28 14:04 spaces file1
-rw-r-----  1 root bandit5 4251 Sep 28 14:04 spaces file2
-rwxr-x---  1 root bandit5 8065 Sep 28 14:04 spaces file3

inhere/maybehere07:
total 56
-rwxr-x---  1 root bandit5 3663 Sep 28 14:04 -file1
-rw-r-----  1 root bandit5 2488 Sep 28 14:04 -file2
-rwxr-x---  1 root bandit5 3362 Sep 28 14:04 -file3
drwxr-x---  2 root bandit5 4096 Sep 28 14:04 .
drwxr-x--- 22 root bandit5 4096 Sep 28 14:04 ..
-rwxr-x---  1 root bandit5 3065 Sep 28 14:04 .file1
-rw-r-----  1 root bandit5 1033 Sep 28 14:04 .file2
-rwxr-x---  1 root bandit5 1997 Sep 28 14:04 .file3
-rwxr-x---  1 root bandit5 4130 Sep 28 14:04 spaces file1
-rw-r-----  1 root bandit5 9064 Sep 28 14:04 spaces file2
-rwxr-x---  1 root bandit5 1022 Sep 28 14:04 spaces file3

inhere/maybehere08:
total 56
-rwxr-x---  1 root bandit5 1077 Sep 28 14:04 -file1
-rw-r-----  1 root bandit5 3825 Sep 28 14:04 -file2
-rwxr-x---  1 root bandit5 2650 Sep 28 14:04 -file3
drwxr-x---  2 root bandit5 4096 Sep 28 14:04 .
drwxr-x--- 22 root bandit5 4096 Sep 28 14:04 ..
-rwxr-x---  1 root bandit5 8169 Sep 28 14:04 .file1
-rw-r-----  1 root bandit5  747 Sep 28 14:04 .file2
-rwxr-x---  1 root bandit5 2217 Sep 28 14:04 .file3
-rwxr-x---  1 root bandit5  215 Sep 28 14:04 spaces file1
-rw-r-----  1 root bandit5 3693 Sep 28 14:04 spaces file2
-rwxr-x---  1 root bandit5 9138 Sep 28 14:04 spaces file3

inhere/maybehere09:
total 76
-rwxr-x---  1 root bandit5 3628 Sep 28 14:04 -file1
-rw-r-----  1 root bandit5  774 Sep 28 14:04 -file2
-rwxr-x---  1 root bandit5 7961 Sep 28 14:04 -file3
drwxr-x---  2 root bandit5 4096 Sep 28 14:04 .
drwxr-x--- 22 root bandit5 4096 Sep 28 14:04 ..
-rwxr-x---  1 root bandit5 6763 Sep 28 14:04 .file1
-rw-r-----  1 root bandit5 8517 Sep 28 14:04 .file2
-rwxr-x---  1 root bandit5 3798 Sep 28 14:04 .file3
-rwxr-x---  1 root bandit5 5301 Sep 28 14:04 spaces file1
-rw-r-----  1 root bandit5 8716 Sep 28 14:04 spaces file2
-rwxr-x---  1 root bandit5 7569 Sep 28 14:04 spaces file3

inhere/maybehere10:
total 56
-rwxr-x---  1 root bandit5 1052 Sep 28 14:04 -file1
-rw-r-----  1 root bandit5 1991 Sep 28 14:04 -file2
-rwxr-x---  1 root bandit5 1237 Sep 28 14:04 -file3
drwxr-x---  2 root bandit5 4096 Sep 28 14:04 .
drwxr-x--- 22 root bandit5 4096 Sep 28 14:04 ..
-rwxr-x---  1 root bandit5 7092 Sep 28 14:04 .file1
-rw-r-----  1 root bandit5   99 Sep 28 14:04 .file2
-rwxr-x---  1 root bandit5 2961 Sep 28 14:04 .file3
-rwxr-x---  1 root bandit5 8269 Sep 28 14:04 spaces file1
-rw-r-----  1 root bandit5 3570 Sep 28 14:04 spaces file2
-rwxr-x---  1 root bandit5 2155 Sep 28 14:04 spaces file3

inhere/maybehere11:
total 72
-rwxr-x---  1 root bandit5 1211 Sep 28 14:04 -file1
-rw-r-----  1 root bandit5 4559 Sep 28 14:04 -file2
-rwxr-x---  1 root bandit5 8854 Sep 28 14:04 -file3
drwxr-x---  2 root bandit5 4096 Sep 28 14:04 .
drwxr-x--- 22 root bandit5 4096 Sep 28 14:04 ..
-rwxr-x---  1 root bandit5  452 Sep 28 14:04 .file1
-rw-r-----  1 root bandit5 2501 Sep 28 14:04 .file2
-rwxr-x---  1 root bandit5 8261 Sep 28 14:04 .file3
-rwxr-x---  1 root bandit5 3147 Sep 28 14:04 spaces file1
-rw-r-----  1 root bandit5  503 Sep 28 14:04 spaces file2
-rwxr-x---  1 root bandit5 8845 Sep 28 14:04 spaces file3

inhere/maybehere12:
total 72
-rwxr-x---  1 root bandit5 9678 Sep 28 14:04 -file1
-rw-r-----  1 root bandit5  251 Sep 28 14:04 -file2
-rwxr-x---  1 root bandit5 9076 Sep 28 14:04 -file3
drwxr-x---  2 root bandit5 4096 Sep 28 14:04 .
drwxr-x--- 22 root bandit5 4096 Sep 28 14:04 ..
-rwxr-x---  1 root bandit5 5815 Sep 28 14:04 .file1
-rw-r-----  1 root bandit5 8244 Sep 28 14:04 .file2
-rwxr-x---  1 root bandit5 1022 Sep 28 14:04 .file3
-rwxr-x---  1 root bandit5 2157 Sep 28 14:04 spaces file1
-rw-r-----  1 root bandit5 2460 Sep 28 14:04 spaces file2
-rwxr-x---  1 root bandit5 1639 Sep 28 14:04 spaces file3

inhere/maybehere13:
total 64
-rwxr-x---  1 root bandit5 1359 Sep 28 14:04 -file1
-rw-r-----  1 root bandit5 1423 Sep 28 14:04 -file2
-rwxr-x---  1 root bandit5 3014 Sep 28 14:04 -file3
drwxr-x---  2 root bandit5 4096 Sep 28 14:04 .
drwxr-x--- 22 root bandit5 4096 Sep 28 14:04 ..
-rwxr-x---  1 root bandit5 5258 Sep 28 14:04 .file1
-rw-r-----  1 root bandit5 8952 Sep 28 14:04 .file2
-rwxr-x---  1 root bandit5 6965 Sep 28 14:04 .file3
-rwxr-x---  1 root bandit5 3952 Sep 28 14:04 spaces file1
-rw-r-----  1 root bandit5  952 Sep 28 14:04 spaces file2
-rwxr-x---  1 root bandit5 4389 Sep 28 14:04 spaces file3

inhere/maybehere14:
total 60
-rwxr-x---  1 root bandit5 4282 Sep 28 14:04 -file1
-rw-r-----  1 root bandit5 8351 Sep 28 14:04 -file2
-rwxr-x---  1 root bandit5 3756 Sep 28 14:04 -file3
drwxr-x---  2 root bandit5 4096 Sep 28 14:04 .
drwxr-x--- 22 root bandit5 4096 Sep 28 14:04 ..
-rwxr-x---  1 root bandit5 3427 Sep 28 14:04 .file1
-rw-r-----  1 root bandit5 1503 Sep 28 14:04 .file2
-rwxr-x---  1 root bandit5 4821 Sep 28 14:04 .file3
-rwxr-x---  1 root bandit5 1382 Sep 28 14:04 spaces file1
-rw-r-----  1 root bandit5  871 Sep 28 14:04 spaces file2
-rwxr-x---  1 root bandit5  376 Sep 28 14:04 spaces file3

inhere/maybehere15:
total 64
-rwxr-x---  1 root bandit5 8794 Sep 28 14:04 -file1
-rw-r-----  1 root bandit5 9499 Sep 28 14:04 -file2
-rwxr-x---  1 root bandit5 6299 Sep 28 14:04 -file3
drwxr-x---  2 root bandit5 4096 Sep 28 14:04 .
drwxr-x--- 22 root bandit5 4096 Sep 28 14:04 ..
-rwxr-x---  1 root bandit5 2159 Sep 28 14:04 .file1
-rw-r-----  1 root bandit5  279 Sep 28 14:04 .file2
-rwxr-x---  1 root bandit5  742 Sep 28 14:04 .file3
-rwxr-x---  1 root bandit5 1623 Sep 28 14:04 spaces file1
-rw-r-----  1 root bandit5   51 Sep 28 14:04 spaces file2
-rwxr-x---  1 root bandit5 1637 Sep 28 14:04 spaces file3

inhere/maybehere16:
total 80
-rwxr-x---  1 root bandit5 4277 Sep 28 14:04 -file1
-rw-r-----  1 root bandit5 5301 Sep 28 14:04 -file2
-rwxr-x---  1 root bandit5 8085 Sep 28 14:04 -file3
drwxr-x---  2 root bandit5 4096 Sep 28 14:04 .
drwxr-x--- 22 root bandit5 4096 Sep 28 14:04 ..
-rwxr-x---  1 root bandit5 5426 Sep 28 14:04 .file1
-rw-r-----  1 root bandit5 8472 Sep 28 14:04 .file2
-rwxr-x---  1 root bandit5 1148 Sep 28 14:04 .file3
-rwxr-x---  1 root bandit5 9773 Sep 28 14:04 spaces file1
-rw-r-----  1 root bandit5 3146 Sep 28 14:04 spaces file2
-rwxr-x---  1 root bandit5 7509 Sep 28 14:04 spaces file3

inhere/maybehere17:
total 72
-rwxr-x---  1 root bandit5 1133 Sep 28 14:04 -file1
-rw-r-----  1 root bandit5 1791 Sep 28 14:04 -file2
-rwxr-x---  1 root bandit5 4422 Sep 28 14:04 -file3
drwxr-x---  2 root bandit5 4096 Sep 28 14:04 .
drwxr-x--- 22 root bandit5 4096 Sep 28 14:04 ..
-rwxr-x---  1 root bandit5  895 Sep 28 14:04 .file1
-rw-r-----  1 root bandit5 8341 Sep 28 14:04 .file2
-rwxr-x---  1 root bandit5 5094 Sep 28 14:04 .file3
-rwxr-x---  1 root bandit5 8361 Sep 28 14:04 spaces file1
-rw-r-----  1 root bandit5 3387 Sep 28 14:04 spaces file2
-rwxr-x---  1 root bandit5 6381 Sep 28 14:04 spaces file3

inhere/maybehere18:
total 68
-rwxr-x---  1 root bandit5 9697 Sep 28 14:04 -file1
-rw-r-----  1 root bandit5   77 Sep 28 14:04 -file2
-rwxr-x---  1 root bandit5 2306 Sep 28 14:04 -file3
drwxr-x---  2 root bandit5 4096 Sep 28 14:04 .
drwxr-x--- 22 root bandit5 4096 Sep 28 14:04 ..
-rwxr-x---  1 root bandit5 5702 Sep 28 14:04 .file1
-rw-r-----  1 root bandit5 2084 Sep 28 14:04 .file2
-rwxr-x---  1 root bandit5  154 Sep 28 14:04 .file3
-rwxr-x---  1 root bandit5 7334 Sep 28 14:04 spaces file1
-rw-r-----  1 root bandit5 6348 Sep 28 14:04 spaces file2
-rwxr-x---  1 root bandit5 7040 Sep 28 14:04 spaces file3

inhere/maybehere19:
total 76
-rwxr-x---  1 root bandit5 6302 Sep 28 14:04 -file1
-rw-r-----  1 root bandit5 5594 Sep 28 14:04 -file2
-rwxr-x---  1 root bandit5 7965 Sep 28 14:04 -file3
drwxr-x---  2 root bandit5 4096 Sep 28 14:04 .
drwxr-x--- 22 root bandit5 4096 Sep 28 14:04 ..
-rwxr-x---  1 root bandit5 7209 Sep 28 14:04 .file1
-rw-r-----  1 root bandit5 4740 Sep 28 14:04 .file2
-rwxr-x---  1 root bandit5  494 Sep 28 14:04 .file3
-rwxr-x---  1 root bandit5 7186 Sep 28 14:04 spaces file1
-rw-r-----  1 root bandit5 8785 Sep 28 14:04 spaces file2
-rwxr-x---  1 root bandit5 2307 Sep 28 14:04 spaces file3
```
so lets try to find the password in all these files 

in **ls** command we have -al for folders and sub dir, -S for Sort Desecnding by Size , -r to reverse the sort to ascending

```shell
bandit5@bandit:~$ ls -alRSr inhere/
inhere/:
total 88
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere19
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere18
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere17
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere16
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere15
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere14
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere13
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere12
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere11
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere10
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere09
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere08
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere07
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere06
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere05
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere04
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere03
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere02
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere01
drwxr-x---  2 root    bandit5 4096 Sep 28 14:04 maybehere00
drwxr-xr-x  4 bandit5 bandit5 4096 Oct  2 20:12 ..
drwxr-x--- 22 root    bandit5 4096 Sep 28 14:04 .

inhere/maybehere19:
total 76
-rwxr-x---  1 root bandit5  494 Sep 28 14:04 .file3
-rwxr-x---  1 root bandit5 2307 Sep 28 14:04 spaces file3
drwxr-x--- 22 root bandit5 4096 Sep 28 14:04 ..
drwxr-x---  2 root bandit5 4096 Sep 28 14:04 .
-rw-r-----  1 root bandit5 4740 Sep 28 14:04 .file2
-rw-r-----  1 root bandit5 5594 Sep 28 14:04 -file2
-rwxr-x---  1 root bandit5 6302 Sep 28 14:04 -file1
-rwxr-x---  1 root bandit5 7186 Sep 28 14:04 spaces file1
-rwxr-x---  1 root bandit5 7209 Sep 28 14:04 .file1
-rwxr-x---  1 root bandit5 7965 Sep 28 14:04 -file3
-rw-r-----  1 root bandit5 8785 Sep 28 14:04 spaces file2

inhere/maybehere18:
total 68
-rw-r-----  1 root bandit5   77 Sep 28 14:04 -file2
-rwxr-x---  1 root bandit5  154 Sep 28 14:04 .file3
-rw-r-----  1 root bandit5 2084 Sep 28 14:04 .file2
-rwxr-x---  1 root bandit5 2306 Sep 28 14:04 -file3
drwxr-x--- 22 root bandit5 4096 Sep 28 14:04 ..
drwxr-x---  2 root bandit5 4096 Sep 28 14:04 .
-rwxr-x---  1 root bandit5 5702 Sep 28 14:04 .file1
-rw-r-----  1 root bandit5 6348 Sep 28 14:04 spaces file2
-rwxr-x---  1 root bandit5 7040 Sep 28 14:04 spaces file3
-rwxr-x---  1 root bandit5 7334 Sep 28 14:04 spaces file1
-rwxr-x---  1 root bandit5 9697 Sep 28 14:04 -file1

inhere/maybehere17:
total 72
-rwxr-x---  1 root bandit5  895 Sep 28 14:04 .file1
-rwxr-x---  1 root bandit5 1133 Sep 28 14:04 -file1
-rw-r-----  1 root bandit5 1791 Sep 28 14:04 -file2
-rw-r-----  1 root bandit5 3387 Sep 28 14:04 spaces file2
drwxr-x--- 22 root bandit5 4096 Sep 28 14:04 ..
drwxr-x---  2 root bandit5 4096 Sep 28 14:04 .
-rwxr-x---  1 root bandit5 4422 Sep 28 14:04 -file3
-rwxr-x---  1 root bandit5 5094 Sep 28 14:04 .file3
-rwxr-x---  1 root bandit5 6381 Sep 28 14:04 spaces file3
-rw-r-----  1 root bandit5 8341 Sep 28 14:04 .file2
-rwxr-x---  1 root bandit5 8361 Sep 28 14:04 spaces file1

inhere/maybehere16:
total 80
-rwxr-x---  1 root bandit5 1148 Sep 28 14:04 .file3
-rw-r-----  1 root bandit5 3146 Sep 28 14:04 spaces file2
drwxr-x--- 22 root bandit5 4096 Sep 28 14:04 ..
drwxr-x---  2 root bandit5 4096 Sep 28 14:04 .
-rwxr-x---  1 root bandit5 4277 Sep 28 14:04 -file1
-rw-r-----  1 root bandit5 5301 Sep 28 14:04 -file2
-rwxr-x---  1 root bandit5 5426 Sep 28 14:04 .file1
-rwxr-x---  1 root bandit5 7509 Sep 28 14:04 spaces file3
-rwxr-x---  1 root bandit5 8085 Sep 28 14:04 -file3
-rw-r-----  1 root bandit5 8472 Sep 28 14:04 .file2
-rwxr-x---  1 root bandit5 9773 Sep 28 14:04 spaces file1

inhere/maybehere15:
total 64
-rw-r-----  1 root bandit5   51 Sep 28 14:04 spaces file2
-rw-r-----  1 root bandit5  279 Sep 28 14:04 .file2
-rwxr-x---  1 root bandit5  742 Sep 28 14:04 .file3
-rwxr-x---  1 root bandit5 1623 Sep 28 14:04 spaces file1
-rwxr-x---  1 root bandit5 1637 Sep 28 14:04 spaces file3
-rwxr-x---  1 root bandit5 2159 Sep 28 14:04 .file1
drwxr-x--- 22 root bandit5 4096 Sep 28 14:04 ..
drwxr-x---  2 root bandit5 4096 Sep 28 14:04 .
-rwxr-x---  1 root bandit5 6299 Sep 28 14:04 -file3
-rwxr-x---  1 root bandit5 8794 Sep 28 14:04 -file1
-rw-r-----  1 root bandit5 9499 Sep 28 14:04 -file2

inhere/maybehere14:
total 60
-rwxr-x---  1 root bandit5  376 Sep 28 14:04 spaces file3
-rw-r-----  1 root bandit5  871 Sep 28 14:04 spaces file2
-rwxr-x---  1 root bandit5 1382 Sep 28 14:04 spaces file1
-rw-r-----  1 root bandit5 1503 Sep 28 14:04 .file2
-rwxr-x---  1 root bandit5 3427 Sep 28 14:04 .file1
-rwxr-x---  1 root bandit5 3756 Sep 28 14:04 -file3
drwxr-x--- 22 root bandit5 4096 Sep 28 14:04 ..
drwxr-x---  2 root bandit5 4096 Sep 28 14:04 .
-rwxr-x---  1 root bandit5 4282 Sep 28 14:04 -file1
-rwxr-x---  1 root bandit5 4821 Sep 28 14:04 .file3
-rw-r-----  1 root bandit5 8351 Sep 28 14:04 -file2

inhere/maybehere13:
total 64
-rw-r-----  1 root bandit5  952 Sep 28 14:04 spaces file2
-rwxr-x---  1 root bandit5 1359 Sep 28 14:04 -file1
-rw-r-----  1 root bandit5 1423 Sep 28 14:04 -file2
-rwxr-x---  1 root bandit5 3014 Sep 28 14:04 -file3
-rwxr-x---  1 root bandit5 3952 Sep 28 14:04 spaces file1
drwxr-x--- 22 root bandit5 4096 Sep 28 14:04 ..
drwxr-x---  2 root bandit5 4096 Sep 28 14:04 .
-rwxr-x---  1 root bandit5 4389 Sep 28 14:04 spaces file3
-rwxr-x---  1 root bandit5 5258 Sep 28 14:04 .file1
-rwxr-x---  1 root bandit5 6965 Sep 28 14:04 .file3
-rw-r-----  1 root bandit5 8952 Sep 28 14:04 .file2

inhere/maybehere12:
total 72
-rw-r-----  1 root bandit5  251 Sep 28 14:04 -file2
-rwxr-x---  1 root bandit5 1022 Sep 28 14:04 .file3
-rwxr-x---  1 root bandit5 1639 Sep 28 14:04 spaces file3
-rwxr-x---  1 root bandit5 2157 Sep 28 14:04 spaces file1
-rw-r-----  1 root bandit5 2460 Sep 28 14:04 spaces file2
drwxr-x--- 22 root bandit5 4096 Sep 28 14:04 ..
drwxr-x---  2 root bandit5 4096 Sep 28 14:04 .
-rwxr-x---  1 root bandit5 5815 Sep 28 14:04 .file1
-rw-r-----  1 root bandit5 8244 Sep 28 14:04 .file2
-rwxr-x---  1 root bandit5 9076 Sep 28 14:04 -file3
-rwxr-x---  1 root bandit5 9678 Sep 28 14:04 -file1

inhere/maybehere11:
total 72
-rwxr-x---  1 root bandit5  452 Sep 28 14:04 .file1
-rw-r-----  1 root bandit5  503 Sep 28 14:04 spaces file2
-rwxr-x---  1 root bandit5 1211 Sep 28 14:04 -file1
-rw-r-----  1 root bandit5 2501 Sep 28 14:04 .file2
-rwxr-x---  1 root bandit5 3147 Sep 28 14:04 spaces file1
drwxr-x--- 22 root bandit5 4096 Sep 28 14:04 ..
drwxr-x---  2 root bandit5 4096 Sep 28 14:04 .
-rw-r-----  1 root bandit5 4559 Sep 28 14:04 -file2
-rwxr-x---  1 root bandit5 8261 Sep 28 14:04 .file3
-rwxr-x---  1 root bandit5 8845 Sep 28 14:04 spaces file3
-rwxr-x---  1 root bandit5 8854 Sep 28 14:04 -file3

inhere/maybehere10:
total 56
-rw-r-----  1 root bandit5   99 Sep 28 14:04 .file2
-rwxr-x---  1 root bandit5 1052 Sep 28 14:04 -file1
-rwxr-x---  1 root bandit5 1237 Sep 28 14:04 -file3
-rw-r-----  1 root bandit5 1991 Sep 28 14:04 -file2
-rwxr-x---  1 root bandit5 2155 Sep 28 14:04 spaces file3
-rwxr-x---  1 root bandit5 2961 Sep 28 14:04 .file3
-rw-r-----  1 root bandit5 3570 Sep 28 14:04 spaces file2
drwxr-x--- 22 root bandit5 4096 Sep 28 14:04 ..
drwxr-x---  2 root bandit5 4096 Sep 28 14:04 .
-rwxr-x---  1 root bandit5 7092 Sep 28 14:04 .file1
-rwxr-x---  1 root bandit5 8269 Sep 28 14:04 spaces file1

inhere/maybehere09:
total 76
-rw-r-----  1 root bandit5  774 Sep 28 14:04 -file2
-rwxr-x---  1 root bandit5 3628 Sep 28 14:04 -file1
-rwxr-x---  1 root bandit5 3798 Sep 28 14:04 .file3
drwxr-x--- 22 root bandit5 4096 Sep 28 14:04 ..
drwxr-x---  2 root bandit5 4096 Sep 28 14:04 .
-rwxr-x---  1 root bandit5 5301 Sep 28 14:04 spaces file1
-rwxr-x---  1 root bandit5 6763 Sep 28 14:04 .file1
-rwxr-x---  1 root bandit5 7569 Sep 28 14:04 spaces file3
-rwxr-x---  1 root bandit5 7961 Sep 28 14:04 -file3
-rw-r-----  1 root bandit5 8517 Sep 28 14:04 .file2
-rw-r-----  1 root bandit5 8716 Sep 28 14:04 spaces file2

inhere/maybehere08:
total 56
-rwxr-x---  1 root bandit5  215 Sep 28 14:04 spaces file1
-rw-r-----  1 root bandit5  747 Sep 28 14:04 .file2
-rwxr-x---  1 root bandit5 1077 Sep 28 14:04 -file1
-rwxr-x---  1 root bandit5 2217 Sep 28 14:04 .file3
-rwxr-x---  1 root bandit5 2650 Sep 28 14:04 -file3
-rw-r-----  1 root bandit5 3693 Sep 28 14:04 spaces file2
-rw-r-----  1 root bandit5 3825 Sep 28 14:04 -file2
drwxr-x--- 22 root bandit5 4096 Sep 28 14:04 ..
drwxr-x---  2 root bandit5 4096 Sep 28 14:04 .
-rwxr-x---  1 root bandit5 8169 Sep 28 14:04 .file1
-rwxr-x---  1 root bandit5 9138 Sep 28 14:04 spaces file3

inhere/maybehere07:
total 56
-rwxr-x---  1 root bandit5 1022 Sep 28 14:04 spaces file3
-rw-r-----  1 root bandit5 1033 Sep 28 14:04 .file2
-rwxr-x---  1 root bandit5 1997 Sep 28 14:04 .file3
-rw-r-----  1 root bandit5 2488 Sep 28 14:04 -file2
-rwxr-x---  1 root bandit5 3065 Sep 28 14:04 .file1
-rwxr-x---  1 root bandit5 3362 Sep 28 14:04 -file3
-rwxr-x---  1 root bandit5 3663 Sep 28 14:04 -file1
drwxr-x--- 22 root bandit5 4096 Sep 28 14:04 ..
drwxr-x---  2 root bandit5 4096 Sep 28 14:04 .
-rwxr-x---  1 root bandit5 4130 Sep 28 14:04 spaces file1
-rw-r-----  1 root bandit5 9064 Sep 28 14:04 spaces file2

inhere/maybehere06:
total 64
-rw-r-----  1 root bandit5 1076 Sep 28 14:04 -file2
-rwxr-x---  1 root bandit5 1271 Sep 28 14:04 .file1
-rwxr-x---  1 root bandit5 2418 Sep 28 14:04 .file3
-rwxr-x---  1 root bandit5 3443 Sep 28 14:04 -file3
-rwxr-x---  1 root bandit5 4073 Sep 28 14:04 spaces file1
drwxr-x--- 22 root bandit5 4096 Sep 28 14:04 ..
drwxr-x---  2 root bandit5 4096 Sep 28 14:04 .
-rw-r-----  1 root bandit5 4251 Sep 28 14:04 spaces file2
-rwxr-x---  1 root bandit5 5731 Sep 28 14:04 -file1
-rwxr-x---  1 root bandit5 8065 Sep 28 14:04 spaces file3
-rw-r-----  1 root bandit5 8976 Sep 28 14:04 .file2

inhere/maybehere05:
total 64
-rwxr-x---  1 root bandit5  880 Sep 28 14:04 spaces file1
-rwxr-x---  1 root bandit5 2346 Sep 28 14:04 -file1
-rw-r-----  1 root bandit5 2420 Sep 28 14:04 spaces file2
-rwxr-x---  1 root bandit5 2572 Sep 28 14:04 -file3
-rwxr-x---  1 root bandit5 3201 Sep 28 14:04 .file1
drwxr-x--- 22 root bandit5 4096 Sep 28 14:04 ..
drwxr-x---  2 root bandit5 4096 Sep 28 14:04 .
-rwxr-x---  1 root bandit5 4585 Sep 28 14:04 .file3
-rw-r-----  1 root bandit5 5917 Sep 28 14:04 .file2
-rw-r-----  1 root bandit5 5959 Sep 28 14:04 -file2
-rwxr-x---  1 root bandit5 8585 Sep 28 14:04 spaces file3

inhere/maybehere04:
total 60
-rwxr-x---  1 root bandit5  142 Sep 28 14:04 .file3
-rwxr-x---  1 root bandit5 2117 Sep 28 14:04 -file3
-rwxr-x---  1 root bandit5 2440 Sep 28 14:04 .file1
-rw-r-----  1 root bandit5 2491 Sep 28 14:04 spaces file2
-rw-r-----  1 root bandit5 2619 Sep 28 14:04 -file2
drwxr-x--- 22 root bandit5 4096 Sep 28 14:04 ..
drwxr-x---  2 root bandit5 4096 Sep 28 14:04 .
-rwxr-x---  1 root bandit5 4410 Sep 28 14:04 -file1
-rwxr-x---  1 root bandit5 5532 Sep 28 14:04 spaces file1
-rwxr-x---  1 root bandit5 6002 Sep 28 14:04 spaces file3
-rw-r-----  1 root bandit5 6144 Sep 28 14:04 .file2

inhere/maybehere03:
total 80
-rwxr-x---  1 root bandit5  315 Sep 28 14:04 -file1
-rwxr-x---  1 root bandit5 2190 Sep 28 14:04 spaces file1
-rwxr-x---  1 root bandit5 2282 Sep 28 14:04 .file3
-rw-r-----  1 root bandit5 3385 Sep 28 14:04 spaces file2
drwxr-x--- 22 root bandit5 4096 Sep 28 14:04 ..
drwxr-x---  2 root bandit5 4096 Sep 28 14:04 .
-rw-r-----  1 root bandit5 6595 Sep 28 14:04 -file2
-rwxr-x---  1 root bandit5 8275 Sep 28 14:04 -file3
-rw-r-----  1 root bandit5 8880 Sep 28 14:04 .file2
-rwxr-x---  1 root bandit5 9234 Sep 28 14:04 spaces file3
-rwxr-x---  1 root bandit5 9769 Sep 28 14:04 .file1

inhere/maybehere02:
total 68
-rwxr-x---  1 root bandit5 2275 Sep 28 14:04 spaces file3
-rw-r-----  1 root bandit5 2577 Sep 28 14:04 .file2
-rw-r-----  1 root bandit5 3511 Sep 28 14:04 -file2
-rwxr-x---  1 root bandit5 3801 Sep 28 14:04 -file1
drwxr-x--- 22 root bandit5 4096 Sep 28 14:04 ..
drwxr-x---  2 root bandit5 4096 Sep 28 14:04 .
-rwxr-x---  1 root bandit5 4932 Sep 28 14:04 -file3
-rwxr-x---  1 root bandit5 6351 Sep 28 14:04 .file1
-rwxr-x---  1 root bandit5 6746 Sep 28 14:04 spaces file1
-rwxr-x---  1 root bandit5 7953 Sep 28 14:04 .file3
-rw-r-----  1 root bandit5 8488 Sep 28 14:04 spaces file2

inhere/maybehere01:
total 80
-rw-r-----  1 root bandit5  288 Sep 28 14:04 -file2
-rw-r-----  1 root bandit5 3070 Sep 28 14:04 .file2
-rwxr-x---  1 root bandit5 3792 Sep 28 14:04 .file3
drwxr-x--- 22 root bandit5 4096 Sep 28 14:04 ..
drwxr-x---  2 root bandit5 4096 Sep 28 14:04 .
-rwxr-x---  1 root bandit5 4139 Sep 28 14:04 spaces file1
-rw-r-----  1 root bandit5 4543 Sep 28 14:04 spaces file2
-rwxr-x---  1 root bandit5 6028 Sep 28 14:04 -file1
-rwxr-x---  1 root bandit5 8834 Sep 28 14:04 spaces file3
-rwxr-x---  1 root bandit5 8944 Sep 28 14:04 .file1
-rwxr-x---  1 root bandit5 9641 Sep 28 14:04 -file3

inhere/maybehere00:
total 72
-rwxr-x---  1 root bandit5  551 Sep 28 14:04 .file1
-rwxr-x---  1 root bandit5 1039 Sep 28 14:04 -file1
-rwxr-x---  1 root bandit5 1915 Sep 28 14:04 spaces file3
drwxr-x--- 22 root bandit5 4096 Sep 28 14:04 ..
drwxr-x---  2 root bandit5 4096 Sep 28 14:04 .
-rwxr-x---  1 root bandit5 4802 Sep 28 14:04 .file3
-rwxr-x---  1 root bandit5 6118 Sep 28 14:04 spaces file1
-rw-r-----  1 root bandit5 6850 Sep 28 14:04 spaces file2
-rwxr-x---  1 root bandit5 7378 Sep 28 14:04 -file3
-rw-r-----  1 root bandit5 7836 Sep 28 14:04 .file2
-rw-r-----  1 root bandit5 9388 Sep 28 14:04 -file2
bandit5@bandit:~$ cat inhere/maybehere07/.file2
DXjZPULLxYr17uwoI01bNLQbtFemEgo7                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      bandit5@bandit:~$ 
```
Matching the File Specs with the files we found the password
