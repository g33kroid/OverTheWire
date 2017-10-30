Well done. You’ve moved past an easy substitution cipher.

The main weakness of a simple substitution cipher is repeated use of a simple key.
In the previous exercise you were able to introduce arbitrary plaintext to expose the key.
In this example, the cipher mechanism is not available to you, the attacker.

However, you have been lucky.
You have intercepted more than one message.
The password to the next level is found in the file ‘krypton4’.
You have also found 3 other files. (found1, found2, found3)

You know the following important details:

The message plaintexts are in English (*** very important) - They were produced from the same key (*** even better!)
Enjoy.

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

