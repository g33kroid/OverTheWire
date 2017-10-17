The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL encryption.

Helpful note: Getting “HEARTBEATING” and “Read R BLOCK”? Use -ign_eof and read the “CONNECTED COMMANDS” section in the manpage.
Next to ‘R’ and ‘Q’, the ‘B’ command also works in this version of that command…

```shell
SSH remote host (hostname or ip address): bandit.labs.overthewire.org                                                    
SSH remote port [22]: 2220                                                                                               
SSH remote username: bandit15                                                                                            
                                                                                                                         
bandit15@bandit.labs.overthewire.org's password:                                                                         
Welcome to Ubuntu 14.04 LTS (GNU/Linux 4.4.0-92-generic x86_64)                                                          
                                                                                                                         
 * Documentation:  https://help.ubuntu.com/                                                                              
                                                                                                                         
The programs included with the Ubuntu system are free software;                                                          
the exact distribution terms for each program are described in the                                                       
individual files in /usr/share/doc/*/copyright.                                                                          
                                                                                                                         
Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by                                                     
applicable law.                                                                                                          
                                                                                                                         
bandit15@bandit:~$ ls -la                                                                                                
total 28                                                                                                                 
drwxr-xr-x  3 bandit15 bandit15 4096 Oct 17 11:23 .
drwxr-xr-x 30 root     root     4096 Oct 17 11:23 ..
-rw-r-----  1 bandit15 bandit15   33 Sep 28 14:04 .bandit14.password                                                     
-rw-r--r--  1 bandit15 bandit15  220 Apr  9  2014 .bash_logout                                                           
-rw-r--r--  1 bandit15 bandit15 3637 Apr  9  2014 .bashrc                                                                
drwx------  2 bandit15 bandit15 4096 Oct 17 11:23 .cache
-rw-r--r--  1 bandit15 bandit15  675 Apr  9  2014 .profile                                                               
bandit15@bandit:~$ cat .bandit14.password                                                                                
4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e 
```
Found Bandit 14 password :D idk why its there but lets see 

okay so it says SSL Connection Lets create self signed SSL

```shell
bandit15@bandit:~$ openssl req -newkey rsa:2048 -nodes -keyout key.pem -x509 -days 365 -out microbot.pem
```
Now Lets Try to Connect 

```shell
bandit15@bandit:~$ openssl s_client -connect localhost:30001 -cert microbot.pem -key key.pem                             
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
    Session-ID: 5CE56AB9C97A1E31E3D6882E282AFF57BA088BF8D39CE86A4E939B2654F1CCE1                                         
    Session-ID-ctx:                                                                                                      
    Master-Key: 9EE98040E2C81510B6944CF6532B7CAFB46A19F41C82E567B5FFABE5CDBE2D769C46799633268C8622AC31E47541696F         
    Key-Arg   : None                                                                                                     
    PSK identity: None                                                                                                   
    PSK identity hint: None                                                                                              
    SRP username: None                                                                                                   
    Start Time: 1508244085                                                                                               
    Timeout   : 300 (sec)                                                                                                
    Verify return code: 18 (self signed certificate)                                                                     
---                                                                                                                      
BfMYroe26WYalil77FoDi9qh59eK5xNr                                                                                         
HEARTBEATING                                                                                                             
read R BLOCK                                                                                                             
read:errno=0                                                                                  
```
It is not as easy as i thought , okay I used the Hint Up if I am getting R Block Statment I should add **ign_eof** to my command 

```shell
bandit15@bandit:~$ openssl s_client -connect localhost:30001 -cert microbot.pem -key key.pem -ign_eof                    
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
    Session-ID: 2E2685B830351729FA62C179B894937BAD943F87D69516F3BE28D2F720F94BD3                                         
    Session-ID-ctx:                                                                                                      
    Master-Key: 64648CD920826DDFCFA15260FA4DE24957EF7FF1D0FC2C952B4EFAFC349F08F27EB6830E3A33F405F9032B269EF9C1D6         
    Key-Arg   : None                                                                                                     
    PSK identity: None                                                                                                   
    PSK identity hint: None                                                                                              
    SRP username: None                                                                                                   
    Start Time: 1508244387                                                                                               
    Timeout   : 300 (sec)                                                                                                
    Verify return code: 18 (self signed certificate)                                                                     
---                                                                                                                      
BfMYroe26WYalil77FoDi9qh59eK5xNr                                                                                         
Correct!                                                                                                                 
cluFn7wTiGryunymYOu4RcffSxQluehd                                                                                         
                                                                                                                         
read:errno=0 
```


