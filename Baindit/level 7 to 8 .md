The password for the next level is stored in the file **data.txt** next to the word **millionth**

```shell
SSH remote host (hostname or ip address): bandit.labs.overthewire.org                                                    
SSH remote port [22]: 2220                                                                                               
SSH remote username: bandit7                                                                                             
                                                                                                                         
bandit7@bandit.labs.overthewire.org's password:                                                                          
Welcome to Ubuntu 14.04 LTS (GNU/Linux 4.4.0-92-generic x86_64)                                                          
                                                                                                                         
 * Documentation:  https://help.ubuntu.com/                                                                              
                                                                                                                         
The programs included with the Ubuntu system are free software;                                                          
the exact distribution terms for each program are described in the                                                       
individual files in /usr/share/doc/*/copyright.                                                                          
                                                                                                                         
Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by                                                     
applicable law.                                                                                                          
                                                                                                                         
bandit7@bandit:~$ ls -la                                                                                                 
total 4112                                                                                                               
drwxr-xr-x  3 bandit7 bandit7    4096 Oct 17 06:48 .
drwxr-xr-x 30 root    root       4096 Oct 17 06:48 ..
-rw-r--r--  1 bandit7 bandit7     220 Apr  9  2014 .bash_logout                                                          
-rw-r--r--  1 bandit7 bandit7    3637 Apr  9  2014 .bashrc                                                               
drwx------  2 bandit7 bandit7    4096 Oct 17 06:48 .cache
-rw-r--r--  1 bandit7 bandit7     675 Apr  9  2014 .profile                                                              
-rw-r-----  1 bandit8 bandit7 4184396 Sep 28 14:04 data.txt                                                              
bandit7@bandit:~$ cat data.txt | grep millionth                                                                          
millionth       cvX2JJa4CFALtqS87jk27qwqGhBM9plV
```
