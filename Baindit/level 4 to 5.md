The password for the next level is stored in the only human-readable file in the inhere directory.
**Tip:** if your terminal is messed up, try the “reset” command. -> reset do terminal reinitialization

```shell
┌─[microbot@parrot]─[~]
└──╼ $sudo ssh  bandit4@bandit.labs.overthewire.org -p 2220
 _                     _ _ _   
| |__   __ _ _ __   __| (_) |_ 
| '_ \ / _` | '_ \ / _` | | __|
| |_) | (_| | | | | (_| | | |_ 
|_.__/ \__,_|_| |_|\__,_|_|\__|
                               
a http://www.overthewire.org wargame.

bandit4@bandit.labs.overthewire.org's password: 
Welcome to Ubuntu 14.04 LTS (GNU/Linux 4.4.0-92-generic x86_64)

 * Documentation:  https://help.ubuntu.com/

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

bandit4@bandit:~$ ls
inhere
bandit4@bandit:~$ 
bandit4@bandit:~$ cd inhere/
bandit4@bandit:~/inhere$ ks
-bash: ks: command not found
bandit4@bandit:~/inhere$ ls
-file00  -file02  -file04  -file06  -file08
-file01  -file03  -file05  -file07  -file09
bandit4@bandit:~/inhere$ ls -la
total 48
-rw-r----- 1 bandit5 bandit4   33 Sep 28 14:04 -file00
-rw-r----- 1 bandit5 bandit4   33 Sep 28 14:04 -file01
-rw-r----- 1 bandit5 bandit4   33 Sep 28 14:04 -file02
-rw-r----- 1 bandit5 bandit4   33 Sep 28 14:04 -file03
-rw-r----- 1 bandit5 bandit4   33 Sep 28 14:04 -file04
-rw-r----- 1 bandit5 bandit4   33 Sep 28 14:04 -file05
-rw-r----- 1 bandit5 bandit4   33 Sep 28 14:04 -file06
-rw-r----- 1 bandit5 bandit4   33 Sep 28 14:04 -file07
-rw-r----- 1 bandit5 bandit4   33 Sep 28 14:04 -file08
-rw-r----- 1 bandit5 bandit4   33 Sep 28 14:04 -file09
drwxr-xr-x 2 root    root    4096 Sep 28 14:04 .
drwxr-xr-x 4 bandit4 bandit4 4096 Oct  2 20:08 ..
bandit4@bandit:~/inhere$ cat ./-file0
cat: ./-file0: No such file or directory
bandit4@bandit:~/inhere$ cat ./-file00
��Cʡ#8�+�����bandit4@bandit:~/inhere$ cat ./-file01
��V��TH��U:�%@J,���O��ca3���C7bandit4@bandit:~/inhere$ cat ./-file02
��㫫�Gd�i���d�����@ǘ��	
                                H�bandit4@bandit:~/inhere$ cat ./-file03
��ֱ����?G[�Og)e�B;�KKjx�g�9��bandit4@bandit:~/inhere$ cat ./-file04
��=G�L�E���z�������̋
                     �0�2��bandit4@bandit:~/inhere$ cat ./-file05
�a��1Sg�å�vs�X��?sC�H�
                       ف�f��bandit4@bandit:~/inhere$ cat ./-file06
���A�`���H@��Cz���-ԕo$/�#�bandit4@bandit:~/inhere$ cat ./-file07
koReBOKuIDDepwhWk7jZC0RTdopnAYKh
bandit4@bandit:~/inhere$ cat ./-file08
��ԥs[*_Y�O����H�Q���[�ג�Q��bandit4@bandit:~/inhere$ cat ./-file09
�}G�b�Wq]��fa�I�#`��fӁ�vo��Qbandit4@bandit:~/inhere$ 
```
