There is a setuid binary in the homedirectory that does the following:
it makes a connection to localhost on the port you specify as a commandline argument.
It then reads a line of text from the connection and compares it to the password in the previous level (bandit20).
If the password is correct, it will transmit the password for the next level (bandit21).

NOTE: Changes to the infrastructure made this level more difficult.
You will need to figure out a way to launch multiple commands in the same Docker instance.

NOTE 2: Try connecting to your own network daemon to see if it works as you think

```shell
┌─[✗]─[microbot@parrot]─[~]
└──╼ $ssh -p 2220 bandit20@bandit.labs.overthewire.org
 _                     _ _ _   
| |__   __ _ _ __   __| (_) |_ 
| '_ \ / _` | '_ \ / _` | | __|
| |_) | (_| | | | | (_| | | |_ 
|_.__/ \__,_|_| |_|\__,_|_|\__|
                               
a http://www.overthewire.org wargame.

bandit20@bandit.labs.overthewire.org's password: 
Welcome to Ubuntu 14.04 LTS (GNU/Linux 4.4.0-92-generic x86_64)

 * Documentation:  https://help.ubuntu.com/

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

bandit20@bandit:~$ ls -la
total 32
drwxr-xr-x  3 bandit20 bandit20 4096 Oct 18 20:07 .
drwxr-xr-x 30 root     root     4096 Oct 18 20:07 ..
-rw-r--r--  1 bandit20 bandit20  220 Apr  9  2014 .bash_logout
-rw-r--r--  1 bandit20 bandit20 3637 Apr  9  2014 .bashrc
drwx------  2 bandit20 bandit20 4096 Oct 18 20:07 .cache
-rw-r--r--  1 bandit20 bandit20  675 Apr  9  2014 .profile
-rwsr-x---  1 bandit21 bandit20 8014 Sep 28 14:04 suconnect
```
This is What we have lets See what is suconnect

```shell
bandit20@bandit:~$ ./suconnect  
Usage: ./suconnect <portnumber>
This program will connect to the given port on localhost using TCP. If it receives the correct password from the other side, the next password is transmitted back.
```
