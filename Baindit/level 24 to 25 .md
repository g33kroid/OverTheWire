A daemon is listening on port 30002 and will give you the password for bandit25
if given the password for bandit24 and a secret numeric 4-digit pincode.
There is no way to retrieve the pincode except by going through all of the 10000 combinations, called brute-forcing.

```shell
bandit24@bandit:~$ nc localhost 30002
I am the pincode checker for user bandit25.
Please enter the password for user bandit24 and the secret pincode on a single line, separated by a space.
```
Note Level 24 Pass : 
