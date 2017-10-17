The password for the next level is stored in the file **data.txt** and is the only line of text that occurs only once

```shell
SSH remote host (hostname or ip address): bandit.labs.overthewire.org                                                    
SSH remote port [22]: 2220                                                                                               
SSH remote username: bandit8                                                                                             
                                                                                                                         
bandit8@bandit.labs.overthewire.org's password:                                                                          
Welcome to Ubuntu 14.04 LTS (GNU/Linux 4.4.0-92-generic x86_64)                                                          
                                                                                                                         
 * Documentation:  https://help.ubuntu.com/                                                                              
                                                                                                                         
The programs included with the Ubuntu system are free software;                                                          
the exact distribution terms for each program are described in the                                                       
individual files in /usr/share/doc/*/copyright.                                                                          
                                                                                                                         
Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by                                                     
applicable law.                                                                                                          
                                                                                                                         
bandit8@bandit:~$ ls -la                                                                                                 
total 60                                                                                                                 
drwxr-xr-x  3 bandit8 bandit8  4096 Oct 17 07:05 .
drwxr-xr-x 30 root    root     4096 Oct 17 07:05 ..
-rw-r--r--  1 bandit8 bandit8   220 Apr  9  2014 .bash_logout                                                            
-rw-r--r--  1 bandit8 bandit8  3637 Apr  9  2014 .bashrc                                                                 
drwx------  2 bandit8 bandit8  4096 Oct 17 07:05 .cache
-rw-r--r--  1 bandit8 bandit8   675 Apr  9  2014 .profile                                                                
-rw-r-----  1 bandit9 bandit8 33033 Sep 28 14:04 data.txt  
bandit8@bandit:~$ sort data.txt | uniq -c | sort                                                                         
      1 UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR                                                                                 
     10 0UHWFwMVia7RNDBxBxFnijhj4tbkNmrE                                                                                 
     10 0pu3J5YMzE8EiAw8ruk9LLOojk45w5ZQ                                                                                 
     10 1a1ho441eF6sXJoNezck3PXv8BaaMR4F                                                                                 
     10 2B24VYv3gOZROipWGBimkP2nbydDtUxf                                                                                 
     10 2Eq0gXKu3Q0Xi7w8fbDeDRKEu8DZGHUn                                                                                 
     10 3TC6KUHgzo0iJKePSv32Z5JyZ1EHbk7j                                                                                 
     10 4E8H678q795jfWGa910ZkdnLo6ZzpDzg                                                                                 
     10 4YdLhz4eXvQkmevfBlhIbvcK1sPEqmsl                                                                                 
     10 4gCvfcpC5IFWHWaGJw1zPgW2xgZC7lkb                                                                                 
     10 4vpnEsPDyypkETWVVhJqRoMIQkJla0FS                                                                                 
     10 5fhJrZAutx4oQMM0puwEnkyfgJk0dOkh                                                                                 
     10 6ACCGZYAdyZKxQoLJ4MUy3hKXUxo0slM                                                                                 
     10 6WYs3owOjVZi7Bte0gIGkgOaT3lyxg4l                                                                                 
     10 7RHcFRZE1iCNCnbSXB0AEaIBf3XvsehE                                                                                 
     10 7RTXt81qWn2e0cji4S3zzsqzwsQqBXPX                                                                                 
     10 7gyBy5Ox9Dd0RDLz07gMceY1FYJiEQzg                                                                                 
     10 83CDe4aTlxOxAPq114IUCtsjVlyGyNZM                                                                                 
     10 9QFQQxpaFXhwPwb1oKJ9sMoCkPeU585h                                                                                 
     10 9Qrtt3DZkKUTjnmgci7lM41ufh1v0cVB                                                                                 
     10 A2buZRlSwTF5bB3czFQfAr96bxQCbj9d                                                                                 
     10 AQZrzHzZOeD0jgcEli4fdnITUzEUgx07                                                                                 
     10 ARIZmdEfoCoFjfMaauUwJasg8n3SEzYC                                                                                 
     10 BLxRSjpo4DYpCWS28Q6VXDTPf8ZyTns4                                                                                 
     10 BY95lO0IPeEgLovOLBrEQKzCNOoasXQJ                                                                                 
     10 CGgqgv6uOKFij5t7a42YsvVLo15nEEMZ                                                                                 
     10 ClizZyHgUP5JyREdM7ZPHaHPnlJuV2Lo                                                                                 
     10 D3yVYusxtP1XcsGVvtnRlUVGom02bBXr                                                                                 
     10 DdTk8Si3D5kWuWECpyvmFTwkoaMb5jZY                                                                                 
     10 E8CmCQFWUawjlHP9q58DGkrf4z5WoBeJ                                                                                 
     10 EX3ix8xLPCrrMGrhh1qrZWTJIttXOiZE                                                                                 
     10 FLHxRBor1UCQL1tCPc4zSzLwitn1YfEd                                                                                 
     10 FN6EFL1UjY0E9OgXqv79nQdrpljIpXs2                                                                                 
     10 FzXDyvlx3bprkHCDot9i4zVxkhKDFuNg                                                                                 
     10 GGJcGnUvo0KORkHoDlOqPGMuUEjMBkoj                                                                                 
     10 HPwT961Lb83sl11VWZDiyOBVSbY5zFIX                                                                                 
     10 Ia8RltFsO91ajiyDjLrUrJftoPbmghdH                                                                                 
     10 If4egxVZHXgQYTLmkLY2Ihp9WECe15nC                                                                                 
     10 J06QeLc7wBvyQ19siMssKQONWznpSVpd                                                                                 
     10 J0Dx1zEoIibvqvNXK6BZ3CTRqsFhoxKI                                                                                 
     10 KP3AR9wsZkhyruqFWXw2F4jEkSmh6sBN                                                                                 
     10 L4yGKL1ItxUpyihIUNoj4BbIQ5Vsk5xO                                                                                 
     10 LV62LtrCTRgy5pRSs4b424QGdABIJP0s                                                                                 
     10 Lnh2oh2NVAHzz7Ia9lLvyfUmTLV8V5jH                                                                                 
     10 M5BOFGgQPjznKNPpkQr8rLloSdwM0MPy                                                                                 
     10 O0tIvuMeshJN6Y4QQw0LnsNSCwAbpGP5                                                                                 
     10 OKFCPPjKGwhSnbgULa6P2K5OV3nfgxJ4                                                                                 
     10 PBZJBaU5RlEUgEjQBv3mwr9Ukmss4FLx                                                                                 
     10 Qbt1WmWuSgvvOJCK46Mt4L17FuOm31ax                                                                                 
     10 QeVgADS2RIN9IUlZMvFeWSogtMfWEkta                                                                                 
     10 S5hBKUYy5pOAhNmz2cV1EvRqHqA38ByR                                                                                 
     10 SAnCyHjSSzRecyaAXpnxL8QSLNjHUe1I                                                                                 
     10 SZl8NOQ2aOrVXwafHXkJ0eTY4hF2SiiW                                                                                 
     10 TkgZWX6C1tqbn8tcdWg59CgeCj6G6GdM                                                                                 
     10 UHCeBxlhQZUh266IDMQWYinseYUWQlQN                                                                                 
     10 UtFrSsji99J6qGOE9l12hnOrc8Xjj69g                                                                                 
     10 VczmfEroPT25d76xyUxr26uXe1XO2xj5                                                                                 
     10 WM49SnzX5SgIRtjZoDgsmXfcmj5tV8Zz                                                                                 
     10 Wc0JYZmT9IPIjNz4rpEoq996fdEMMHWq                                                                                 
     10 WndnL0koY4zDUcxH6sjWSH4f2WcurHKu                                                                                 
     10 XcDVE5g6YDw3tzlUBT8WahExD9EbsS7R                                                                                 
     10 Y6NdlGMkNJlRHfH5821S2D0urWg00AOo                                                                                 
     10 ZHwihiPYW9AJBUjSXRfYWVXBHpk5ESWC                                                                                 
     10 ZOMmLix3dpVjDTtStrNqRwfZRg3MLdRL                                                                                 
     10 ZSg2m6GrdCCyrRUBOF8gCk8qZHsairv8                                                                                 
     10 ZVNjuI1lqhBq7vWIEtLO4EFrXNh1lbaJ                                                                                 
     10 ZqZxHU1cdykKQbXYe9aE56LIwCd8CzcA                                                                                 
     10 ZzljQaPkmv86QTsWfesDMdkYbfxqm9hk                                                                                 
     10 aGPFIfnEmyfYesfTLgyhTwgzRvczy7nw                                                                                 
     10 ckbF9qrmbRH6mjb93cNZsI6CxLhCtexV                                                                                 
     10 dJK3tZD6JNAw7DfSLtLIi5sRhH7BQk2F                                                                                 
     10 dlIe4NexJXWf9ritCR6ly3f4yiRmtGRF                                                                                 
     10 eDDRMCn1e9YgIu68PxbjiUHJfEtbtVwp                                                                                 
     10 f9M40PC9sdaLn7KRqZPNxrtPkeUbM8hi                                                                                 
     10 gPhGpdXLJ8ex4aNwUL74F9pEXmdjR4oD                                                                                 
     10 gPkHdZKVt5sFgO7dXcQj6AE6Kz1zupWY                                                                                 
     10 htiNLQhrCd8nWaRTdL5ErMFQp8pvV0PP                                                                                 
     10 iDAnhcpsZnPpMnlPUIhhpmuEtWTevoMa                                                                                 
     10 iq30DgYR7MRxOK4ck1FaW3hyTbCQaUI8                                                                                 
     10 jGtCD7C4vgCmXNK679qAZA30VIQ7gqr5                                                                                 
     10 jYUGqz2Jw0jAgOVsf5ZKIWd5z9NqwXVL                                                                                 
     10 lPMyg6yuXgNNohITPrzepoxWAlVNcKb7                                                                                 
     10 mI42t7siphZg8xCG6gMAUSesNDT5iayx                                                                                 
     10 mYrxaugs90Mo5apTJgTZCCAS4lme7Obm                                                                                 
     10 pYHOHnbQh07GAlk3LOSu6kIafYu4EAzY                                                                                 
     10 q22hhiQiy6zwyCMcIweLXdvuxe2yReOm                                                                                 
     10 qI8Q9vbuxJgeoCLTj9XLa1sElf7f9OW6                                                                                 
     10 rBVGO5zuqpOv6EXPfWi4zheUO3hUT4dZ                                                                                 
     10 rVSvYd7BaMWQ9RTd5IotCPxssbjk8i52                                                                                 
     10 rhyJx2g1v61bnaFqQFgzuFOUWERsznlC                                                                                 
     10 sTldm4Wt3NIeCOcqgneNuow7pmj2L5xh                                                                                 
     10 sVZHmFrIyr6O7Haa6E2wCkXE5SJwwY1K                                                                                 
     10 sxW5T665dRUCtAaKVOaYeIKShi7IwzZH                                                                                 
     10 tDZv38vz8H9pZOidZKpMRXva3ihFpiZg                                                                                 
     10 v9CFv1878nEQGYDspfazPTkoBxdoIfLr                                                                                 
     10 vXCfS9smMx3BWjZOzUGHyJCjSxG3eObn                                                                                 
     10 vn8mRxa4YVik4vtCyrSdz1bGRN71lgUu                                                                                 
     10 vwgcvhlnP9DJ9wNQJgYkVpAvrd5WTzHf                                                                                 
     10 xBzuRR0vEg07m0j5DUywU8VgPKA0faZI                                                                                 
     10 xg4dS7lEFqXKmT4CWuoRtNAPIu556bmS                                                                                 
     10 yLFRVdVJ2AA8PGGcLaRXDaN49qlV4tPd    
bandit8@bandit:~$ sort data.txt | uniq -c | sort | grep -v 10                                                            
      1 UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR       
```
Bingo :D 
