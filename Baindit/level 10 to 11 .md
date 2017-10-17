The password for the next level is stored in the file data.txt, which contains base64 encoded data

```shell
SSH remote host (hostname or ip address): bandit.labs.overthewire.org                                                    
SSH remote port [22]: 2220                                                                                               
SSH remote username: bandit10                                                                                            
                                                                                                                         
bandit10@bandit.labs.overthewire.org's password:                                                                         
Welcome to Ubuntu 14.04 LTS (GNU/Linux 4.4.0-92-generic x86_64)                                                          
                                                                                                                         
 * Documentation:  https://help.ubuntu.com/                                                                              
                                                                                                                         
The programs included with the Ubuntu system are free software;                                                          
the exact distribution terms for each program are described in the                                                       
individual files in /usr/share/doc/*/copyright.                                                                          
                                                                                                                         
Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by                                                     
applicable law.                                                                                                          
                                                                                                                         
bandit10@bandit:~$ ls -la                                                                                                
total 28                                                                                                                 
drwxr-xr-x  3 bandit10 bandit10 4096 Oct 17 07:52 .
drwxr-xr-x 30 root     root     4096 Oct 17 07:52 ..
-rw-r--r--  1 bandit10 bandit10  220 Apr  9  2014 .bash_logout                                                           
-rw-r--r--  1 bandit10 bandit10 3637 Apr  9  2014 .bashrc                                                                
drwx------  2 bandit10 bandit10 4096 Oct 17 07:52 .cache
-rw-r--r--  1 bandit10 bandit10  675 Apr  9  2014 .profile                                                               
-rw-r-----  1 bandit11 bandit10   69 Sep 28 14:04 data.txt

bandit10@bandit:~$ cat data.txt                                                                                          
VGhlIHBhc3N3b3JkIGlzIElGdWt3S0dzRlc4TU9xM0lSRnFyeEUxaHhUTkViVVBSCg==     

bandit10@bandit:~$ cat data.txt | base64 -d                                                                              
The password is IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR      
```
