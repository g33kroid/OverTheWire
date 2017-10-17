The password for the next level is stored in the file data.txt in one of the few human-readable strings,
beginning with several ‘=’ characters.

```shell
SSH remote host (hostname or ip address): bandit.labs.overthewire.org                                                    
SSH remote port [22]: 2220                                                                                                                      
SSH remote username: bandit9                                                                                                                    
                                                                                                                                                
bandit9@bandit.labs.overthewire.org's password:                                                                                                 
Welcome to Ubuntu 14.04 LTS (GNU/Linux 4.4.0-92-generic x86_64)                                                                                 
                                                                                                                                                
 * Documentation:  https://help.ubuntu.com/                                                                                                     
                                                                                                                                                
The programs included with the Ubuntu system are free software;                                                                                 
the exact distribution terms for each program are described in the                                                                              
individual files in /usr/share/doc/*/copyright.                                                                                                 
                                                                                                                                                
Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by                                                                            
applicable law.                                                                                                                                 
                                                                                                                                                
bandit9@bandit:~$ ls -la                                                                                                                        
total 44                                                                                                                                        
drwxr-xr-x  3 bandit9  bandit9  4096 Oct 17 07:28 .
drwxr-xr-x 30 root     root     4096 Oct 17 07:28 ..
-rw-r--r--  1 bandit9  bandit9   220 Apr  9  2014 .bash_logout                                                                                  
-rw-r--r--  1 bandit9  bandit9  3637 Apr  9  2014 .bashrc                                                                                       
drwx------  2 bandit9  bandit9  4096 Oct 17 07:28 .cache
-rw-r--r--  1 bandit9  bandit9   675 Apr  9  2014 .profile                                                                                      
-rw-r-----  1 bandit10 bandit9 19379 Sep 28 14:04 data.txt        

bandit9@bandit:~$ strings data.txt | grep -F '='                                                                         
|========== the
,]=NB
@k<=
"m=g
========== password
=r-3
========== is
mu=v.
<= V57
i=Hk>$B
========== truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk
S1N=
PbgQ=Zp
=M Q
x3X}=
```
