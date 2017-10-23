A program is running automatically at regular intervals from cron, the time-based job scheduler.
Look in /etc/cron.d/ for the configuration and see what command is being executed.

```shell
bandit20@bandit:~$ ssh -p 2220 bandit21@localhost                                                                        
The authenticity of host '[localhost]:2220 ([127.0.0.1]:2220)' can't be established.                                     
ECDSA key fingerprint is ee:4c:8c:e7:57:2c:bc:63:24:b8:e6:23:27:63:72:9f.                                                
Are you sure you want to continue connecting (yes/no)? yes                                                               
Warning: Permanently added '[localhost]:2220' (ECDSA) to the list of known hosts.                                        
 _                     _ _ _                                                                                             
| |__   __ _ _ __   __| (_) |_                                                                                           
| '_ \ / _` | '_ \ / _` | | __|                                                                                          
| |_) | (_| | | | | (_| | | |_                                                                                           
|_.__/ \__,_|_| |_|\__,_|_|\__|                                                                                          

a http://www.overthewire.org wargame.                                                                                    
                                                                                                                         
bandit21@localhost's password:                                                                                           

      ,----..            ,----,          .---.                                                                           
     /   /   \         ,/   .`|         /. ./|                                                                           
    /   .     :      ,`   .'  :     .--'.  ' ;                                                                           
   .   /   ;.  \   ;    ;     /    /__./ \ : |                                                                           
  .   ;   /  ` ; .'___,/    ,' .--'.  '   \' .                                                                           
  ;   |  ; \ ; | |    :     | /___/ \ |    ' '                                                                           
  |   :  | ; | ' ;    |.';  ; ;   \  \;      :                                                                           
  .   |  ' ' ' : `----'  |  |  \   ;  `      |                                                                           
  '   ;  \; /  |     '   :  ;   .   \    .\  ;                                                                           
   \   \  ',  /      |   |  '    \   \   ' \ |                                                                           
    ;   :    /       '   :  |     :   '  |--"                                                                            
     \   \ .'        ;   |.'       \   \ ;                                                                               
  www. `---` ver     '---' he       '---" ire.org                                                                        


Welcome to the OverTheWire games machine!                                                                                
                                                                                                                         
If you find any problems, please report them to Steven on                                                                
irc.overthewire.org.                                                                                                     
                                                                                                                         
--[ Playing the games ]--                                                                                                
                                                                                                                         
  This machine holds several wargames.                                                                                   
  If you are playing "somegame", then:                                                                                   
                                                                                                                         
    * USERNAMES are somegame0, somegame1, ...                                                                            
    * Most LEVELS are stored in /somegame/.                                                                              
    * PASSWORDS for each level are stored in /etc/somegame_pass/.                                                        
                                                                                                                         
  Write-access to homedirectories is disabled. It is advised to create a                                                 
  working directory with a hard-to-guess name in /tmp/.  You can use the                                                 
  command "mktemp -d" in order to generate a random and hard to guess                                                    
  directory in /tmp/.  Read-access to both /tmp/ and /proc/ is disabled                                                  
  so that users can not snoop on eachother.                                                                              
                                                                                                                         
  Please play nice:                                                                                                      

    * don't leave orphan processes running                                                                               
    * don't leave exploit-files laying around                                                                            
    * don't annoy other players                                                                                          
    * don't post passwords or spoilers                                                                                   
                                                                                                                         
--[ Tips ]--                                                                                                             
                                                                                                                         
  This machine has a 64bit processor and many security-features enabled                                                  
  by default, although ASLR has been switched off.  The following                                                        
  compiler flags might be interesting:                                                                                   
                                                                                                                         
    -m32                    compile for 32bit                                                                            
    -fno-stack-protector    disable ProPolice                                                                            
    -Wl,-z,norelro          disable relro                                                                                
                                                                                                                         
  In addition, the execstack tool can be used to flag the stack as                                                       
  executable on ELF binaries.                                                                                            
                                                                                                                         
  Finally, network-access is limited for most levels by a local                                                          
  firewall.                                                                                                              
                                                                                                                         
--[ Tools ]--                                                                                                            
                                                                                                                         
 For your convenience we have installed a few usefull tools which you can find                                           
 in the following locations:                                                                                             
                                                                                                                         
    * peda (https://github.com/longld/peda) in /usr/local/peda/                                                          
    * gdbinit (https://github.com/gdbinit/Gdbinit) in /usr/local/gdbinit/                                                
    * pwntools (https://github.com/Gallopsled/pwntools) in /usr/local/pwntools/                                          
    * radare2 (http://www.radare.org/) should be in $PATH                                                                
                                                                                                                         
--[ More information ]--                                                                                                 
                                                                                                                         
  For more information regarding individual wargames, visit                                                              
  http://www.overthewire.org/wargames/                                                                                   
                                                                                                                         
  For questions or comments, contact us through IRC on                                                                   
  irc.overthewire.org.                                                                                                   
                                                                                                                         
                                                                                                                         
The programs included with the Ubuntu system are free software;                                                          
the exact distribution terms for each program are described in the                                                       
individual files in /usr/share/doc/*/copyright.                                                                          
                                                                                                                         
Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by                                                     
applicable law.                                                                                                          
                                                                                                                         
bandit21@bandit:~$ ls -la                                                                                                
total 28                                                                                                                 
drwxr-xr-x  3 bandit21 bandit21 4096 Oct 23 09:09 .
drwxr-xr-x 31 root     root     4096 Oct 23 09:09 ..
-rw-r--r--  1 bandit21 bandit21  220 Apr  9  2014 .bash_logout                                                           
-rw-r--r--  1 bandit21 bandit21 3637 Apr  9  2014 .bashrc                                                                
drwx------  2 bandit21 bandit21 4096 Oct 23 09:09 .cache
-r--------  1 bandit21 bandit21   33 Sep 28 14:04 .prevpass                                                              
-rw-r--r--  1 bandit21 bandit21  675 Apr  9  2014 .profile  
```
Lets Check the Cron.d Directory 

```shell
bandit21@bandit:~$ ls -la /etc/cron.d/                                                                                   
total 32                                                                                                                 
drwxr-xr-x   2 root root 4096 Sep 28 14:04 .
drwxr-xr-x 119 root root 4096 Oct 23 08:27 ..
-rw-r--r--   1 root root  102 Feb  9  2013 .placeholder                                                                  
-rw-r--r--   1 root root  355 May 25  2013 cron-apt                                                                      
-rw-r--r--   1 root root  120 Sep 28 14:04 cronjob_bandit22                                                              
-rw-r--r--   1 root root  122 Sep 28 14:04 cronjob_bandit23                                                              
-rw-r--r--   1 root root  120 Sep 28 14:04 cronjob_bandit24                                                              
-rw-r--r--   1 root root  510 Aug  4 20:03 php5                                                                          
```
Checking cronjob_bandit22 
```shell
bandit21@bandit:~$ cat /etc/cron.d/cronjob_bandit22                                                                      
@reboot bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null                                                               
* * * * * bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null      
```
it run a script in /usr/bin and put the output to /dev/null

lets go ahead and read that script 
```shell
bandit21@bandit:~$ cat /usr/bin/cronjob_bandit22.sh                                                                      
#!/bin/bash                                                                                                              
chmod 644 /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv                                                                          
cat /etc/bandit_pass/bandit22 > /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv    
```
Lets Run it 
```shell
bandit21@bandit:~$ sh /usr/bin/cronjob_bandit22.sh                                                                       
chmod: changing permissions of '/tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv': Operation not permitted                          
/usr/bin/cronjob_bandit22.sh: 3: /usr/bin/cronjob_bandit22.sh: cannot create /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv: Permi
ssion denied 
```
Permission Denied but who cares we have the password :D 
