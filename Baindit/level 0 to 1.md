Connect with SSH to the Machine **bandit.labs.overthewire.org** , on port **2220**. The **username is bandit0** and the 
**password is bandit0.**

## Level 0 -> 1

**The password for the next level is stored in a file called readme located in the home directory.**

```shell
┌─[✗]─[microbot@parrot]─[~]
└──╼ $ssh  bandit0@bandit.labs.overthewire.org -p 2220
 _                     _ _ _   
| |__   __ _ _ __   __| (_) |_ 
| '_ \ / _` | '_ \ / _` | | __|
| |_) | (_| | | | | (_| | | |_ 
|_.__/ \__,_|_| |_|\__,_|_|\__|
                               
a http://www.overthewire.org wargame.

bandit0@bandit.labs.overthewire.org's password: 
Welcome to Ubuntu 14.04 LTS (GNU/Linux 4.4.0-92-generic x86_64)

 * Documentation:  https://help.ubuntu.com/

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

bandit0@bandit:~$ ls
readme
bandit0@bandit:~$ cat readme 
boJ9jbbUNNfktd78OOpsqOltutMc3MY1
```
