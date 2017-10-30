The password for level 2 is in the file ‘krypton2’. It is ‘encrypted’ using a simple rotation.
It is also in non-standard ciphertext format.
When using alpha characters for cipher text it is normal to group the letters into 5 letter clusters, regardless of word boundaries.
This helps obfuscate any patterns. This file has kept the plain text word boundaries and carried them to the cipher text. Enjoy!

```shell
krypton1@krypton:~$ ls -la
total 24
drwxr-xr-x  3 krypton1 krypton1 4096 Oct 30 11:11 .
drwxr-xr-x 10 root     root     4096 Oct 30 11:11 ..
-rw-r--r--  1 krypton1 krypton1  220 Apr  9  2014 .bash_logout
-rw-r--r--  1 krypton1 krypton1 3637 Apr  9  2014 .bashrc
drwx------  2 krypton1 krypton1 4096 Oct 30 11:11 .cache
-rw-r--r--  1 krypton1 krypton1  675 Apr  9  2014 .profile
```
File is not here lets find it somewhere else 

```shell
krypton1@krypton:/$ ls
README.txt  boot  dev  home     lib    lib64   media  opt   root  sbin  sys  usr
bin         d     etc  krypton  lib32  libx32  mnt    proc  run   srv   tmp  var
krypton1@krypton:/$ cd krypton/
krypton1@krypton:/krypton$ ls
krypton1  krypton2  krypton3  krypton4  krypton5  krypton6
krypton1@krypton:/krypton$ cd krypton1
krypton1@krypton:/krypton/krypton1$ ls -la
total 16
drwxr-xr-x 2 root     root     4096 Oct 30 04:15 .
drwxr-xr-x 8 root     root     4096 Oct 30 04:15 ..
-rw-r----- 1 krypton1 krypton1  882 Oct 30 04:15 README
-rw-r----- 1 krypton1 krypton1   26 Oct 30 04:15 krypton2
```
lets check README

```text
krypton1@krypton:/krypton/krypton1$ cat README
Welcome to Krypton!

This game is intended to give hands on experience with cryptography
and cryptanalysis.  The levels progress from classic ciphers, to modern,
easy to harder.

Although there are excellent public tools, like cryptool,to perform
the simple analysis, we strongly encourage you to try and do these
without them for now.  We will use them in later excercises.

** Please try these levels without cryptool first **


The first level is easy.  The password for level 2 is in the file
'krypton2'.  It is 'encrypted' using a simple rotation called ROT13.
It is also in non-standard ciphertext format.  When using alpha characters for
cipher text it is normal to group the letters into 5 letter clusters,
regardless of word boundaries.  This helps obfuscate any patterns.

This file has kept the plain text word boundaries and carried them to
the cipher text.

Enjoy!
```
krypton1@krypton:/krypton/krypton1$ cat krypton2
YRIRY GJB CNFFJBEQ EBGGRA
```
Now Lets Check Planet Calc https://planetcalc.com/1434/

```text
ROT13	LEVEL TWO PASSWORD ROTTEN
```
