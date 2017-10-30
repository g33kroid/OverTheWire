Krypton 2

ROT13 is a simple substitution cipher.

Substitution ciphers are a simple replacement algorithm.  In this example
of a substitution cipher, we will explore a 'monoalphebetic' cipher.
Monoalphebetic means, literally, "one alphabet" and you will see why.

This level contains an old form of cipher called a 'Caesar Cipher'.
A Caesar cipher shifts the alphabet by a set number.  For example:

plain:  a b c d e f g h i j k ...
cipher: G H I J K L M N O P Q ...

In this example, the letter 'a' in plaintext is replaced by a 'G' in the
ciphertext so, for example, the plaintext 'bad' becomes 'HGJ' in ciphertext.

The password for level 3 is in the file krypton3.  It is in 5 letter
group ciphertext.  It is encrypted with a Caesar Cipher.  Without any
further information, this cipher text may be difficult to break.  You do
not have direct access to the key, however you do have access to a program
that will encrypt anything you wish to give it using the key.
If you think logically, this is completely easy.

One shot can solve it!

Have fun.

Additional Information:

The `encrypt` binary will look for the keyfile in your current working
directory. Therefore, it might be best to create a working direcory in /tmp
and in there a link to the keyfile. As the `encrypt` binary runs setuid
`krypton3`, you also need to give `krypton3` access to your working directory.

Here is an example:
```shell
krypton2@melinda:~$ mktemp -d
/tmp/tmp.Wf2OnCpCDQ
krypton2@melinda:~$ cd /tmp/tmp.Wf2OnCpCDQ
krypton2@melinda:/tmp/tmp.Wf2OnCpCDQ$ ln -s /krypton/krypton2/keyfile.dat
krypton2@melinda:/tmp/tmp.Wf2OnCpCDQ$ ls
keyfile.dat
krypton2@melinda:/tmp/tmp.Wf2OnCpCDQ$ chmod 777 .
krypton2@melinda:/tmp/tmp.Wf2OnCpCDQ$ /krypton/krypton2/encrypt /etc/issue
krypton2@melinda:/tmp/tmp.Wf2OnCpCDQ$ ls
ciphertext  keyfile.dat
```
Lets Start
```shell
krypton2@krypton:/krypton/krypton2$ cd ~
krypton2@krypton:~$ mktemp -d
/tmp/tmp.12MPROw9aU
krypton2@krypton:~$ cd /tmp/tmp.12MPROw9aU
krypton2@krypton:/tmp/tmp.12MPROw9aU$ ln -s /krypton/krypton2/keyfile.dat
krypton2@krypton:/tmp/tmp.12MPROw9aU$ ls
keyfile.dat
krypton2@krypton:/tmp/tmp.12MPROw9aU$ chmod 777
chmod: missing operand after '777'
Try 'chmod --help' for more information.
krypton2@krypton:/tmp/tmp.12MPROw9aU$ chmod 777 .
krypton2@krypton:/tmp/tmp.12MPROw9aU$ cat /etc/issue
Ubuntu 14.04.5 LTS \n \l

krypton2@krypton:/tmp/tmp.12MPROw9aU$ /krypton/krypton2/encrypt /etc/issue
krypton2@krypton:/tmp/tmp.12MPROw9aU$ ls
ciphertext  keyfile.dat
krypton2@krypton:/tmp/tmp.12MPROw9aU$ cat ciphertext
GNGZFGXFEZX
krypton2@krypton:/tmp/tmp.12MPROw9aU$ nano dummy
krypton2@krypton:/tmp/tmp.12MPROw9aU$ /krypton/krypton2/encrypt dummy
krypton2@krypton:/tmp/tmp.12MPROw9aU$ ls
ciphertext  dummy  keyfile.dat
```
So the above steps were mentioned to create tmp file and link the key to make sure it worked now 

Lets test the encryption
```
krypton2@krypton:/tmp/tmp.12MPROw9aU$ cat dummy
foo
krypton2@krypton:/tmp/tmp.12MPROw9aU$ cat ciphertext
RAA
```
so F -> R and O -> A

One More Test
```shell
krypton2@krypton:/tmp/tmp.12MPROw9aU$ cat dummyy
asd
krypton2@krypton:/tmp/tmp.12MPROw9aU$ cat ciphertext
MEP
```
so A -> M and S -> E and d -> P 

Now I can predict the letters pattern but why should i waste time when the encryption can give it to me straight 
```shell
krypton2@krypton:/tmp/tmp.12MPROw9aU$ cat dummy
abcdefghijklmnopqrstuvwxyz
krypton2@krypton:/tmp/tmp.12MPROw9aU$ cat ciphertext
MNOPQRSTUVWXYZABCDEFGHIJKL
```
Now its fully mapped for small letters What if Caps Letters
```shell
krypton2@krypton:/tmp/tmp.aimnQsPIDK$ cat dummy
ABCDEFGHIJKLMNOPQRSTUVWXYZ
krypton2@krypton:/tmp/tmp.aimnQsPIDK$ cat ciphertext
MNOPQRSTUVWXYZABCDEFGHIJKL
```
so it doesn't check the case now since we have the mapping let decrypt the password 
```shell
krypton2@krypton:/tmp/tmp.aimnQsPIDK$ cat /krypton/krypton2/krypton3
OMQEMDUEQMEK
```
We can decrypt it by hand or i created a simple script to decrypt the key

```python
dic = {'M':'A','N':'B','O':'C','P':'D','Q':'E','R':'F','S':'G','T':'H',
'U':'I','V':'J','W':'K','X':'L','Y':'M','Z':'N',
'A':'O','B':'P','C':'Q','D':'R','E':'S','F':'T','G':'U','H':'V','I':'W',
'J':'X','K':'Y','L':'Z'}
encflag = "OMQEMDUEQMEK"

flag = ""
for i in encflag:
    flag = flag + dic[i]

print (flag)
```
And here is our flag
```shell
CAESARISEASY
```

