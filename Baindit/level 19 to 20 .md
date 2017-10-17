To gain access to the next level, you should use the setuid binary in the homedirectory.
Execute it without arguments to find out how to use it.
The password for this level can be found in the usual place (/etc/bandit_pass),
after you have used the setuid binary.

```shell
bandit17@bandit:~$ ssh bandit19@localhost -p 2220      
The authenticity of host '[localhost]:2220 ([127.0.0.1]:2220)' can't be established.
ECDSA key fingerprint is ee:4c:8c:e7:57:2c:bc:63:24:b8:e6:23:27:63:72:9f.
Are you sure you want to continue connecting (yes/no)? yes
Failed to add the host to the list of known hosts (/home/bandit17/.ssh/known_hosts).
 _                     _ _ _   
| |__   __ _ _ __   __| (_) |_ 
| '_ \ / _` | '_ \ / _` | | __|
| |_) | (_| | | | | (_| | | |_ 
|_.__/ \__,_|_| |_|\__,_|_|\__|
                               
a http://www.overthewire.org wargame.

@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@         WARNING: UNPROTECTED PRIVATE KEY FILE!          @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
Permissions 0640 for '/home/bandit17/.ssh/id_rsa' are too open.
It is required that your private key files are NOT accessible by others.
This private key will be ignored.
bad permissions: ignore key: /home/bandit17/.ssh/id_rsa
bandit19@localhost's password: 
               
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

bandit19@bandit:~$ ls -la
total 32
drwxr-xr-x  3 bandit19 bandit19 4096 Oct 17 20:43 .
drwxr-xr-x 33 root     root     4096 Oct 17 20:43 ..
-rw-r--r--  1 bandit19 bandit19  220 Apr  9  2014 .bash_logout
-rw-r--r--  1 bandit19 bandit19 3637 Apr  9  2014 .bashrc
drwx------  2 bandit19 bandit19 4096 Oct 17 20:43 .cache
-rw-r--r--  1 bandit19 bandit19  675 Apr  9  2014 .profile
-rwsr-x---  1 bandit20 bandit19 7378 Sep 28 14:04 bandit20-do

bandit19@bandit:~$ file bandit20-do 
bandit20-do: setuid ELF 32-bit LSB  executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.24, BuildID[sha1]=eaeb8602df7360a72be0da10457afd946b39a1a5, not stripped

bandit19@bandit:~$ ./bandit20-do 
Run a command as another user.
  Example: ./bandit20-do id

bandit19@bandit:~$ ./bandit20-do id
uid=11019(bandit19) gid=11019(bandit19) euid=11020(bandit20) groups=11020(bandit20),11019(bandit19)

bandit19@bandit:~$ ./bandit20-do ls /etc/bandit_pass/
bandit0   bandit11  bandit14  bandit17	bandit2   bandit22  bandit25  bandit4  bandit7
bandit1   bandit12  bandit15  bandit18	bandit20  bandit23  bandit26  bandit5  bandit8
bandit10  bandit13  bandit16  bandit19	bandit21  bandit24  bandit3   bandit6  bandit9

bandit19@bandit:~$ ./bandit20-do cat /etc/bandit_pass/bandit20 
GbKksEFF4yrVs6il55v6gwY5aVje5f0j
```
