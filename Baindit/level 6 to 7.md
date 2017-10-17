The password for the next level is stored somewhere on the server and has all of the following properties:

owned by user bandit7

owned by group bandit6

33 bytes in size
    
```shell
SSH remote host (hostname or ip address): bandit.labs.overthewire.org                                                    
SSH remote port [22]: 2220                                                                                               
SSH remote username: bandit6                                                                                             
                                                                                                                         
bandit6@bandit.labs.overthewire.org's password:                                                                          
Welcome to Ubuntu 14.04 LTS (GNU/Linux 4.4.0-92-generic x86_64)                                                          
                                                                                                                         
 * Documentation:  https://help.ubuntu.com/                                                                              
                                                                                                                         
The programs included with the Ubuntu system are free software;                                                          
the exact distribution terms for each program are described in the                                                       
individual files in /usr/share/doc/*/copyright.                                                                          
                                                                                                                         
Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by                                                     
applicable law.                                                                                                          
                                                                                                                         
bandit6@bandit:~$ ls -la                                                                                                 
total 24                                                                                                                 
drwxr-xr-x  3 bandit6 bandit6 4096 Oct 17 05:46 .
drwxr-xr-x 30 root    root    4096 Oct 17 05:46 ..
-rw-r--r--  1 bandit6 bandit6  220 Apr  9  2014 .bash_logout                                                             
-rw-r--r--  1 bandit6 bandit6 3637 Apr  9  2014 .bashrc                                                                  
drwx------  2 bandit6 bandit6 4096 Oct 17 05:46 .cache
-rw-r--r--  1 bandit6 bandit6  675 Apr  9  2014 .profile
bandit6@bandit:~$ cd ..                                                                                                  
bandit6@bandit:/home$ ls                                                                                                 
bandit0   bandit11  bandit14  bandit17  bandit2   bandit22  bandit25  bandit4  bandit7
bandit1   bandit12  bandit15  bandit18  bandit20  bandit23  bandit26  bandit5  bandit8
bandit10  bandit13  bandit16  bandit19  bandit21  bandit24  bandit3   bandit6  bandit9
bandit6@bandit:/home$ cd ..
bandit6@bandit:/$ find / -user bandit7 -group bandit6 2> /dev/null                                                       
/var/lib/dpkg/info/bandit7.password                                                                                      
bandit6@bandit:/$ cat /var/lib/dpkg/info/bandit7.password                                                                
HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs                                    
```
**NOTE** We Passed the Output to /dev/null so that every exception or error message raised will not be displayed in termainal to have a clean output of where the file we are looking for is located 
