There are 2 files in the homedirectory: passwords.old and passwords.new.
The password for the next level is in passwords.new and
is the only line that has been changed between passwords.old and passwords.new

NOTE: if you have solved this level and see ‘Byebye!’ when trying to log into bandit18,
this is related to the next level, bandit19

```shell
bandit16@bandit:/tmp/microbot$ ssh -i ssh-keyl.private bandit17@localhost
The authenticity of host 'localhost (127.0.0.1)' can't be established.
ECDSA key fingerprint is ee:4c:8c:e7:57:2c:bc:63:24:b8:e6:23:27:63:72:9f.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'localhost' (ECDSA) to the list of known hosts.
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


The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

bandit17@bandit:~$ ls -la
total 44
drwxr-xr-x  4 bandit17 bandit17 4096 Oct 17 20:12 .
drwxr-xr-x 31 root     root     4096 Oct 17 20:12 ..
-rw-r-----  1 bandit17 bandit17   33 Sep 28 14:04 .bandit16.password
-rw-r--r--  1 bandit17 bandit17  220 Apr  9  2014 .bash_logout
-rw-r--r--  1 bandit17 bandit17 3637 Apr  9  2014 .bashrc
drwx------  2 bandit17 bandit17 4096 Oct 17 20:12 .cache
-rw-r--r--  1 bandit17 bandit17  675 Apr  9  2014 .profile
drwxr-xr-x  2 root     root     4096 Sep 28 14:04 .ssh
-rw-r-----  1 bandit17 bandit17 1704 Sep 28 14:04 .ssl-cert-snakeoil.key
-rw-r-----  1 bandit18 bandit17 3300 Sep 28 14:04 passwords.new
-rw-r-----  1 bandit18 bandit17 3300 Sep 28 14:04 passwords.old
bandit17@bandit:~$ man diff
bandit17@bandit:~$ diff passwords.new passwords.old  
42c42
< kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd                --- Give us Bye Bye
---
> R3GQabj3vKRTcjTTISWvO1RJWc5sqSXO               --- Give us permission denied

```
