The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions

```shell
SSH remote host (hostname or ip address): bandit.labs.overthewire.org                                                    
SSH remote port [22]: 2220                                                                                               
SSH remote username: bandit11                                                                                            
                                                                                                                         
bandit11@bandit.labs.overthewire.org's password:                                                                         
Welcome to Ubuntu 14.04 LTS (GNU/Linux 4.4.0-92-generic x86_64)                                                          
                                                                                                                         
 * Documentation:  https://help.ubuntu.com/                                                                              
                                                                                                                         
The programs included with the Ubuntu system are free software;                                                          
the exact distribution terms for each program are described in the                                                       
individual files in /usr/share/doc/*/copyright.                                                                          
                                                                                                                         
Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by                                                     
applicable law.                                                                                                          
                                                                                                                         
bandit11@bandit:~$ ls -la                                                                                                
total 28                                                                                                                 
drwxr-xr-x  3 bandit11 bandit11 4096 Oct 17 08:09 .
drwxr-xr-x 30 root     root     4096 Oct 17 08:09 ..
-rw-r--r--  1 bandit11 bandit11  220 Apr  9  2014 .bash_logout                                                           
-rw-r--r--  1 bandit11 bandit11 3637 Apr  9  2014 .bashrc                                                                
drwx------  2 bandit11 bandit11 4096 Oct 17 08:09 .cache
-rw-r--r--  1 bandit11 bandit11  675 Apr  9  2014 .profile                                                               
-rw-r-----  1 bandit12 bandit11   49 Sep 28 14:04 data.txt                                                               
bandit11@bandit:~$ cat data.txt                                                                                          
Gur cnffjbeq vf 5Gr8L4qetPEsPk8htqjhRK8XSP6x2RHh    
```
Using Planet Calc Decryptor : https://planetcalc.com/1434/
The Decrypted Statment : **ROT13	The password is 5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu**
