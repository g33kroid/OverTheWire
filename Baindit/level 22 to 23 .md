A program is running automatically at regular intervals from cron, the time-based job scheduler.
Look in /etc/cron.d/ for the configuration and see what command is being executed.

NOTE: Looking at shell scripts written by other people is a very useful skill.
The script for this level is intentionally made easy to read. If you are having problems understanding what it does, 
try executing it to see the debug information it prints.

```shell
bandit21@bandit:~$ ssh -p 2220 bandit22@localhost                                                                        
 _                     _ _ _                                                                                             
| |__   __ _ _ __   __| (_) |_                                                                                           
| '_ \ / _` | '_ \ / _` | | __|                                                                                          
| |_) | (_| | | | | (_| | | |_                                                                                           
|_.__/ \__,_|_| |_|\__,_|_|\__|                                                                                          

a http://www.overthewire.org wargame.                                                                                    
                                                                                                                         
bandit22@localhost's password:                                                                                           

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
                                                                                                                         
bandit22@bandit:~$ ls -la                                                                                                
total 24                                                                                                                 
drwxr-xr-x  3 bandit22 bandit22 4096 Oct 23 09:41 .
drwxr-xr-x 32 root     root     4096 Oct 23 09:41 ..
-rw-r--r--  1 bandit22 bandit22  220 Apr  9  2014 .bash_logout                                                           
-rw-r--r--  1 bandit22 bandit22 3637 Apr  9  2014 .bashrc                                                                
drwx------  2 bandit22 bandit22 4096 Oct 23 09:41 .cache
-rw-r--r--  1 bandit22 bandit22  675 Apr  9  2014 .profile 
```
Nothing useful lets head to /etc/cron.d/

```shell
bandit22@bandit:~$ ls -la /etc/cron.d/                                                                                   
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

Reading cronjob_bandit23

```shell
bandit22@bandit:~$ cat /etc/cron.d/cronjob_bandit23                                                                      
@reboot bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null                                                              
* * * * * bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null  
```
Lets Read the shell script 

```shell
bandit22@bandit:~$ cat /usr/bin/cronjob_bandit23.sh                                                                      
#!/bin/bash                                                                                                              
                                                                                                                         
myname=$(whoami)                                                                                                         
mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)                                                            
                                                                                                                         
echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"                                                   
                                                                                                                         
cat /etc/bandit_pass/$myname > /tmp/$mytarget    
```

Easy to It get username hash it as md5 create a /tmp/file with that name and put the password there

Lets Run the Script but first get our name from the machine 

```shell
bandit22@bandit:~$ whoami                                                                                                
bandit22  
```
Running the Script 

```shell
bandit22@bandit:~$ sh /usr/bin/cronjob_bandit23.sh                                                                       
Copying passwordfile /etc/bandit_pass/bandit22 to /tmp/8169b67bd894ddbb4412f91573b38db3                                  
bandit22@bandit:~$ cat /tmp/8169b67bd894ddbb4412f91573b38db3                                                             
Yk7owGAcWjwMVRwrTesJEwB7WVOiILLI   
```

But it Gave me Bandit 22 Password not bandit 23 Password, lets try to edit the script (Permission Denied) 

So this has nothing to do with cron and crontab 

all what i did was execute the script manually but change whoami with bandit 23 so all what we needed is the echo statmet 

```shell
bandit22@bandit:~$ cat /usr/bin/cronjob_bandit23.sh | grep echo                                                          
mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)
echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"
bandit22@bandit:~$ echo I am user bandit23 | md5sum | cut -d ' ' -f 1                                                    
8ca319486bfbbc3663ea0fbe81326349                                                                                         
bandit22@bandit:~$ cat /tmp/8ca319486bfbbc3663ea0fbe81326349                                                             
jc1udXuA1tiHqjIsL8yaapX5XIAI6i0n        
```
instead of I am user (Whoami) which is bandit22 we execute it manually and change it to bandit23
