The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.

```shell
bandit13@bandit:~$ ssh -i sshkey.private -p 2220 bandit14@bandit.labs.overthewire.org                                    
 _                     _ _ _                                                                                             
| |__   __ _ _ __   __| (_) |_                                                                                           
| '_ \ / _` | '_ \ / _` | | __|                                                                                          
| |_) | (_| | | | | (_| | | |_                                                                                           
|_.__/ \__,_|_| |_|\__,_|_|\__|                                                                                          

a http://www.overthewire.org wargame.                                                                                    
                                                                                                                         

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
                                                                                                                         
bandit14@bandit:~$
```
We are connected using level 13 ssh key lets try to solve this level

Searching for the Password File 

```shell
bandit14@bandit:/$ find / -user bandit14 2> dev/null | more                                                              
/etc/bandit_pass/bandit14                                                                                                
/home/bandit13/sshkey.private                                                                                            
/home/bandit14                                                                                                           
/home/bandit14/.bash_history                                                                                             
/home/bandit14/.cache                                                                                                    
/home/bandit14/.cache/motd.legal-displayed                                                                               
/home/bandit14/.ssh/authorized_keys                                                                                      
/home/bandit14/.profile                                                                                                  
/home/bandit14/.bashrc                                                                                                   
/home/bandit14/.bash_logout                                                                                              
/dev/pts/1                                                                                                               
/proc/2960                                                                                                               
/proc/2960/task                                                                                                          
/proc/2960/task/2960                                                                                                     
/proc/2960/task/2960/net                                                                                                 
/proc/2960/task/2960/attr                                                                                                
/proc/2960/net                                                                                                           
/proc/2960/attr                                                                                                          
/proc/2961                                                                                                               
/proc/2961/task                                                                                                          
/proc/2961/task/2961                                                                                                     
/proc/2961/task/2961/fd                                                                                                  
^C
``` 
Its The First File (Current Password)
```shell
bandit14@bandit:/$ cat /etc/bandit_pass/bandit14                                                                         
4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e   
```

Now Lets Submit it to the Service running on port *30000* on *localhost*

```shell
bandit14@bandit:/$ nc localhost 30000                                                                                    
4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e                                                                                         
Correct!                                                                                                                 
BfMYroe26WYalil77FoDi9qh59eK5xNr            
```

