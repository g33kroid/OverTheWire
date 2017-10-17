The credentials for the next level can be retrieved by submitting the password of the current level to a port on localhost in the range 31000 to 32000.
First find out which of these ports have a server listening on them. Then find out which of those speak SSL and which don’t.
There is only 1 server that will give the next credentials,
the others will simply send back to you whatever you send to it.

```shell
SSH remote host (hostname or ip address): bandit.labs.overthewire.org                                                    
SSH remote port [22]: 2220                                                                                               
SSH remote username: bandit16                                                                                            
                                                                                                                         
bandit16@bandit.labs.overthewire.org's password:                                                                         
Welcome to Ubuntu 14.04 LTS (GNU/Linux 4.4.0-92-generic x86_64)                                                          
                                                                                                                         
 * Documentation:  https://help.ubuntu.com/                                                                              
                                                                                                                         
The programs included with the Ubuntu system are free software;                                                          
the exact distribution terms for each program are described in the                                                       
individual files in /usr/share/doc/*/copyright.                                                                          
                                                                                                                         
Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by                                                     
applicable law.                                                                                                          
                                                                                                                         
bandit16@bandit:~$ ls -la                                                                                                
total 32                                                                                                                 
drwxr-xr-x  3 bandit16 bandit16 4096 Oct 17 13:10 .
drwxr-xr-x 30 root     root     4096 Oct 17 13:10 ..
-rw-r-----  1 bandit16 bandit16   33 Sep 28 14:04 .bandit15.password                                                     
-rw-r--r--  1 bandit16 bandit16  220 Apr  9  2014 .bash_logout                                                           
-rw-r--r--  1 bandit16 bandit16 3637 Apr  9  2014 .bashrc                                                                
drwx------  2 bandit16 bandit16 4096 Oct 17 13:10 .cache
-rw-r--r--  1 bandit16 bandit16  675 Apr  9  2014 .profile                                                               
-rw-r-----  1 bandit16 bandit16 1704 Sep 28 14:04 .ssl-cert-snakeoil.key
```
Lets Go ahead and Scan the localhost for any service

```shell
bandit16@bandit:~$ nmap -p 31000-32000 127.0.0.1                                                                         
                                                                                                                         
Starting Nmap 6.40 ( http://nmap.org ) at 2017-10-17 13:13 UTC                                                           
Nmap scan report for localhost (127.0.0.1)                                                                               
Host is up (0.00068s latency).                                                                                           
Not shown: 996 closed ports                                                                                              
PORT      STATE SERVICE                                                                                                  
31046/tcp open  unknown                                                                                                  
31518/tcp open  unknown                                                                                                  
31691/tcp open  unknown                                                                                                  
31790/tcp open  unknown                                                                                                  
31960/tcp open  unknown
```
Lets Try to get any service details or version

```shell
bandit16@bandit:~$ nmap -sV -p 31000-32000 127.0.0.1                                                                     
                                                                                                                         
Starting Nmap 6.40 ( http://nmap.org ) at 2017-10-17 13:14 UTC                                                           
Stats: 0:00:41 elapsed; 0 hosts completed (1 up), 1 undergoing Service Scan                                              
Service scan Timing: About 40.00% done; ETC: 13:15 (0:01:02 remaining)                                                   
Nmap scan report for localhost (127.0.0.1)                                                                               
Host is up (0.00074s latency).                                                                                           
Not shown: 996 closed ports                                                                                              
PORT      STATE SERVICE VERSION                                                                                          
31046/tcp open  echo                                                                                                     
31518/tcp open  msdtc   Microsoft Distributed Transaction Coordinator (error)                                            
31691/tcp open  echo                                                                                                     
31790/tcp open  msdtc   Microsoft Distributed Transaction Coordinator (error)                                            
31960/tcp open  echo                                                                                                     
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows                                                                 
                                                                                                                         
Service detection performed. Please report any incorrect results at http://nmap.org/submit/ .                            
Nmap done: 1 IP address (1 host up) scanned in 41.24 seconds 
```
Perfect so Out of 5 ports only 3 we are looking at :D or maybe all , Connecting to ECHO ports first 

```shell
bandit16@bandit:~$ openssl s_client -connect localhost:31046 -cert certificate.pem -key key.pem -ign_eof                 
CONNECTED(00000003)                                                                                                      
140737354053280:error:140770FC:SSL routines:SSL23_GET_SERVER_HELLO:unknown protocol:s23_clnt.c:795:                      
---                                                                                                                      
no peer certificate available                                                                                            
---                                                                                                                      
No client certificate CA names sent                                                                                      
---                                                                                                                      
SSL handshake has read 7 bytes and written 295 bytes                                                                     
---                                                                                                                      
New, (NONE), Cipher is (NONE)                                                                                            
Secure Renegotiation IS NOT supported                                                                                    
Compression: NONE                                                                                                        
Expansion: NONE                                                                                                          
---                                                                                                                      
bandit16@bandit:~$ openssl s_client -connect localhost:31619 -cert certificate.pem -key key.pem -ign_eof                 
connect: Connection refused                                                                                              
connect:errno=111                                                                                                        
bandit16@bandit:~$ openssl s_client -connect localhost:31960 -cert certificate.pem -key key.pem -ign_eof                 
CONNECTED(00000003)                                                                                                      
140737354053280:error:140770FC:SSL routines:SSL23_GET_SERVER_HELLO:unknown protocol:s23_clnt.c:795:                      
---                                                                                                                      
no peer certificate available                                                                                            
---                                                                                                                      
No client certificate CA names sent                                                                                      
---                                                                                                                      
SSL handshake has read 7 bytes and written 295 bytes                                                                     
---                                                                                                                      
New, (NONE), Cipher is (NONE)                                                                                            
Secure Renegotiation IS NOT supported                                                                                    
Compression: NONE                                                                                                        
Expansion: NONE                                                                                                          
---                                                                                                                      
bandit16@bandit:~$ openssl s_client -connect localhost:31790 -cert certificate.pem -key key.pem -ign_eof                 
CONNECTED(00000003)                                                                                                      
depth=0 CN = 8f75dc271013                                                                                                
verify error:num=18:self signed certificate                                                                              
verify return:1                                                                                                          
depth=0 CN = 8f75dc271013                                                                                                
verify return:1                                                                                                          
---                                                                                                                      
Certificate chain                                                                                                        
 0 s:/CN=8f75dc271013                                                                                                    
   i:/CN=8f75dc271013                                                                                                    
---                                                                                                                      
Server certificate                                                                                                       
-----BEGIN CERTIFICATE-----                                                                                              
MIICvjCCAaagAwIBAgIJALADbwWQ0u9aMA0GCSqGSIb3DQEBCwUAMBcxFTATBgNV                                                         
BAMTDDhmNzVkYzI3MTAxMzAeFw0xNzA5MTYwNzAyMjRaFw0yNzA5MTQwNzAyMjRa                                                         
MBcxFTATBgNVBAMTDDhmNzVkYzI3MTAxMzCCASIwDQYJKoZIhvcNAQEBBQADggEP                                                         
ADCCAQoCggEBALmjBUTlmjROJUssm+rAlFADFfzrz+xCH0qUXryou5/wW8pnQ6nG                                                         
HbdeRIBwTVGFiDIKRbFdWQU4BbrfjEhyGn9d7eh/3GV09ZdvLDYRoLmJ4tDF8CiC                                                         
wGl9GufcWr3zeaNYa8CwVdtWam8umhMICrsv7B5iV9RdSQfudUtVbr26SBVyuhBm                                                         
m0t7Su6rLCrrGtshdIihjk4k67bBMpSNAOduhpp79UgIPKcwJUhRJHTcji3m/IQ8                                                         
O9zNS25oL8KhMn7e/Xe70kztstq0ShMsx8feutONnGulUOlaEMMqW+HSWgnVeG/r                                                         
mU9Nzwn++4qxe16OvvmXAzctH2RlDx7XbcsCAwEAAaMNMAswCQYDVR0TBAIwADAN                                                         
BgkqhkiG9w0BAQsFAAOCAQEADHODX5CcMLI5fdumzly5FAVg5Yc22eDGNhmyhi/N                                                         
kDhP6QYw+HW5nWEYapc9m/ZQGEEoxr+wj6qeEhscxRxpuEIcunZsLKcoAmToyXeO                                                         
ANMslQugRcGqN57Pt0h5VuctLMa3ickeVPFvV6gxJSHBNRK1iN8nrfsy+zR+stzI                                                         
xcjIuakDDxMKFtb/1TMKf4/EsimSQLS0WXLjbxfQ/J510O4/Of0tmZI0ZIG+cKmM                                                         
V5hAOtuuAk6jREfWYJQ3DB+phv7PO9s2FpofVJss5PK4NWDS7UQOv359ZOJ85ZpJ                                                         
ihGxDqV7IAHJZNM9lvFXz/+EOn1oTGW9V8bAwt34OVYoPw==                                                                         
-----END CERTIFICATE-----                                                                                                
subject=/CN=8f75dc271013                                                                                                 
issuer=/CN=8f75dc271013                                                                                                  
---                                                                                                                      
No client certificate CA names sent                                                                                      
---                                                                                                                      
SSL handshake has read 1682 bytes and written 637 bytes                                                                  
---                                                                                                                      
New, TLSv1/SSLv3, Cipher is DHE-RSA-AES256-SHA                                                                           
Server public key is 2048 bit                                                                                            
Secure Renegotiation IS supported                                                                                        
Compression: NONE                                                                                                        
Expansion: NONE                                                                                                          
SSL-Session:                                                                                                             
    Protocol  : SSLv3                                                                                                    
    Cipher    : DHE-RSA-AES256-SHA                                                                                       
    Session-ID: 2C93F3833B1F1C28DD43C6BDFF07069E8F6B71ED1A8C791AA5C71FE166BCE16D                                         
    Session-ID-ctx:                                                                                                      
    Master-Key: 3EDD72B64D81EBF23D44ECE7AA38B9C15D049004AA39A7679D50058B9091F98A289C2751FF85225FE75744C74F72F6F4         
    Key-Arg   : None                                                                                                     
    PSK identity: None                                                                                                   
    PSK identity hint: None                                                                                              
    SRP username: None                                                                                                   
    Start Time: 1508247398                                                                                               
    Timeout   : 300 (sec)                                                                                                
    Verify return code: 18 (self signed certificate)                                                                     
---                                                                                                                      
cluFn7wTiGryunymYOu4RcffSxQluehd                                                                                         
Correct!                                                                                                                 
-----BEGIN RSA PRIVATE KEY-----                                                                                          
MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ                                                         
imZzeyGC0gtZPGujUSxiJSWI/oTqexh+cAMTSMlOJf7+BrJObArnxd9Y7YT2bRPQ                                                         
Ja6Lzb558YW3FZl87ORiO+rW4LCDCNd2lUvLE/GL2GWyuKN0K5iCd5TbtJzEkQTu                                                         
DSt2mcNn4rhAL+JFr56o4T6z8WWAW18BR6yGrMq7Q/kALHYW3OekePQAzL0VUYbW                                                         
JGTi65CxbCnzc/w4+mqQyvmzpWtMAzJTzAzQxNbkR2MBGySxDLrjg0LWN6sK7wNX                                                         
x0YVztz/zbIkPjfkU1jHS+9EbVNj+D1XFOJuaQIDAQABAoIBABagpxpM1aoLWfvD                                                         
KHcj10nqcoBc4oE11aFYQwik7xfW+24pRNuDE6SFthOar69jp5RlLwD1NhPx3iBl                                                         
J9nOM8OJ0VToum43UOS8YxF8WwhXriYGnc1sskbwpXOUDc9uX4+UESzH22P29ovd                                                         
d8WErY0gPxun8pbJLmxkAtWNhpMvfe0050vk9TL5wqbu9AlbssgTcCXkMQnPw9nC                                                         
YNN6DDP2lbcBrvgT9YCNL6C+ZKufD52yOQ9qOkwFTEQpjtF4uNtJom+asvlpmS8A                                                         
vLY9r60wYSvmZhNqBUrj7lyCtXMIu1kkd4w7F77k+DjHoAXyxcUp1DGL51sOmama                                                         
+TOWWgECgYEA8JtPxP0GRJ+IQkX262jM3dEIkza8ky5moIwUqYdsx0NxHgRRhORT                                                         
8c8hAuRBb2G82so8vUHk/fur85OEfc9TncnCY2crpoqsghifKLxrLgtT+qDpfZnx                                                         
SatLdt8GfQ85yA7hnWWJ2MxF3NaeSDm75Lsm+tBbAiyc9P2jGRNtMSkCgYEAypHd                                                         
HCctNi/FwjulhttFx/rHYKhLidZDFYeiE/v45bN4yFm8x7R/b0iE7KaszX+Exdvt                                                         
SghaTdcG0Knyw1bpJVyusavPzpaJMjdJ6tcFhVAbAjm7enCIvGCSx+X3l5SiWg0A                                                         
R57hJglezIiVjv3aGwHwvlZvtszK6zV6oXFAu0ECgYAbjo46T4hyP5tJi93V5HDi                                                         
Ttiek7xRVxUl+iU7rWkGAXFpMLFteQEsRr7PJ/lemmEY5eTDAFMLy9FL2m9oQWCg                                                         
R8VdwSk8r9FGLS+9aKcV5PI/WEKlwgXinB3OhYimtiG2Cg5JCqIZFHxD6MjEGOiu                                                         
L8ktHMPvodBwNsSBULpG0QKBgBAplTfC1HOnWiMGOU3KPwYWt0O6CdTkmJOmL8Ni                                                         
blh9elyZ9FsGxsgtRBXRsqXuz7wtsQAgLHxbdLq/ZJQ7YfzOKU4ZxEnabvXnvWkU                                                         
YOdjHdSOoKvDQNWu6ucyLRAWFuISeXw9a/9p7ftpxm0TSgyvmfLF2MIAEwyzRqaM                                                         
77pBAoGAMmjmIJdjp+Ez8duyn3ieo36yrttF5NSsJLAbxFpdlc1gvtGCWW+9Cq0b                                                         
dxviW8+TFVEBl1O4f7HVm6EpTscdDxU+bCXWkfjuRb7Dy9GOtt9JPsX8MBTakzh3                                                         
vBgsyi/sN3RqRBcGU40fOoZyfAMT8s1m/uYv52O6IgeuZ/ujbjY=                                                                     
-----END RSA PRIVATE KEY-----                                                                                            
                                                                                                                         
read:errno=0                                                                                                             
bandit16@bandit:~$ nano recv.key                                                                                         
bandit16@bandit:~$ ls                                                                                                    
certificate.pem  key.pem                                                                                                 
bandit16@bandit:~$ openssl s_client -connect localhost:31518 -cert certificate.pem -key key.pem -ign_eof                 
CONNECTED(00000003)                                                                                                      
depth=0 CN = 8f75dc271013                                                                                                
verify error:num=18:self signed certificate                                                                              
verify return:1                                                                                                          
depth=0 CN = 8f75dc271013                                                                                                
verify return:1                                                                                                          
---                                                                                                                      
Certificate chain                                                                                                        
 0 s:/CN=8f75dc271013                                                                                                    
   i:/CN=8f75dc271013                                                                                                    
---                                                                                                                      
Server certificate                                                                                                       
-----BEGIN CERTIFICATE-----                                                                                              
MIICvjCCAaagAwIBAgIJALADbwWQ0u9aMA0GCSqGSIb3DQEBCwUAMBcxFTATBgNV                                                         
BAMTDDhmNzVkYzI3MTAxMzAeFw0xNzA5MTYwNzAyMjRaFw0yNzA5MTQwNzAyMjRa                                                         
MBcxFTATBgNVBAMTDDhmNzVkYzI3MTAxMzCCASIwDQYJKoZIhvcNAQEBBQADggEP                                                         
ADCCAQoCggEBALmjBUTlmjROJUssm+rAlFADFfzrz+xCH0qUXryou5/wW8pnQ6nG                                                         
HbdeRIBwTVGFiDIKRbFdWQU4BbrfjEhyGn9d7eh/3GV09ZdvLDYRoLmJ4tDF8CiC                                                         
wGl9GufcWr3zeaNYa8CwVdtWam8umhMICrsv7B5iV9RdSQfudUtVbr26SBVyuhBm                                                         
m0t7Su6rLCrrGtshdIihjk4k67bBMpSNAOduhpp79UgIPKcwJUhRJHTcji3m/IQ8                                                         
O9zNS25oL8KhMn7e/Xe70kztstq0ShMsx8feutONnGulUOlaEMMqW+HSWgnVeG/r                                                         
mU9Nzwn++4qxe16OvvmXAzctH2RlDx7XbcsCAwEAAaMNMAswCQYDVR0TBAIwADAN                                                         
BgkqhkiG9w0BAQsFAAOCAQEADHODX5CcMLI5fdumzly5FAVg5Yc22eDGNhmyhi/N                                                         
kDhP6QYw+HW5nWEYapc9m/ZQGEEoxr+wj6qeEhscxRxpuEIcunZsLKcoAmToyXeO                                                         
ANMslQugRcGqN57Pt0h5VuctLMa3ickeVPFvV6gxJSHBNRK1iN8nrfsy+zR+stzI                                                         
xcjIuakDDxMKFtb/1TMKf4/EsimSQLS0WXLjbxfQ/J510O4/Of0tmZI0ZIG+cKmM                                                         
V5hAOtuuAk6jREfWYJQ3DB+phv7PO9s2FpofVJss5PK4NWDS7UQOv359ZOJ85ZpJ                                                         
ihGxDqV7IAHJZNM9lvFXz/+EOn1oTGW9V8bAwt34OVYoPw==                                                                         
-----END CERTIFICATE-----                                                                                                
subject=/CN=8f75dc271013                                                                                                 
issuer=/CN=8f75dc271013                                                                                                  
---                                                                                                                      
No client certificate CA names sent                                                                                      
---                                                                                                                      
SSL handshake has read 1682 bytes and written 637 bytes                                                                  
---                                                                                                                      
New, TLSv1/SSLv3, Cipher is DHE-RSA-AES256-SHA                                                                           
Server public key is 2048 bit                                                                                            
Secure Renegotiation IS supported                                                                                        
Compression: NONE                                                                                                        
Expansion: NONE                                                                                                          
SSL-Session:                                                                                                             
    Protocol  : SSLv3                                                                                                    
    Cipher    : DHE-RSA-AES256-SHA                                                                                       
    Session-ID: 7ABA769DDB71E60D2706E46C525A7B701BB5F275145AF76B378EA505ECD2019C                                         
    Session-ID-ctx:                                                                                                      
    Master-Key: A5AF03617CCE6DDB32E326708D6C8576AE15CD9A0DC44DC2F6EB454A49A63635772801EF2BC1BF2E5226AA49D2096E63         
    Key-Arg   : None                                                                                                     
    PSK identity: None                                                                                                   
    PSK identity hint: None                                                                                              
    SRP username: None                                                                                                   
    Start Time: 1508247525                                                                                               
    Timeout   : 300 (sec)                                                                                                
    Verify return code: 18 (self signed certificate)                                                                     
---                                                                                                                      
cluFn7wTiGryunymYOu4RcffSxQluehd                                                                                         
cluFn7wTiGryunymYOu4RcffSxQluehd                                                                                         
something                                                                                                                
something                                                                                                                
^C                           
```
