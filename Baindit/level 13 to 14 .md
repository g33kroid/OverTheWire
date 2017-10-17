The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14.
For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level.
Note: localhost is a hostname that refers to the machine you are working on

```shell
SSH remote host (hostname or ip address): bandit.labs.overthewire.org                                                    
SSH remote port [22]: 2220                                                                                               
SSH remote username: bandit13                                                                                            
                                                                                                                         
bandit13@bandit.labs.overthewire.org's password:                                                                         
Welcome to Ubuntu 14.04 LTS (GNU/Linux 4.4.0-92-generic x86_64)                                                          
                                                                                                                         
 * Documentation:  https://help.ubuntu.com/                                                                              
                                                                                                                         
The programs included with the Ubuntu system are free software;                                                          
the exact distribution terms for each program are described in the                                                       
individual files in /usr/share/doc/*/copyright.                                                                          
                                                                                                                         
Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by                                                     
applicable law.                                                                                                          
                                                                                                                         
bandit13@bandit:~$ ls -la                                                                                                
total 28                                                                                                                 
drwxr-xr-x  3 bandit13 bandit13 4096 Oct 17 09:56 .
drwxr-xr-x 30 root     root     4096 Oct 17 09:56 ..
-rw-r--r--  1 bandit13 bandit13  220 Apr  9  2014 .bash_logout                                                           
-rw-r--r--  1 bandit13 bandit13 3637 Apr  9  2014 .bashrc                                                                
drwx------  2 bandit13 bandit13 4096 Oct 17 09:56 .cache
-rw-r--r--  1 bandit13 bandit13  675 Apr  9  2014 .profile                                                               
-rw-r-----  1 bandit14 bandit13 1679 Sep 28 14:04 sshkey.private                                                         
bandit13@bandit:~$ cat sshkey.private                                                                                    
-----BEGIN RSA PRIVATE KEY-----                                                                                          
MIIEpAIBAAKCAQEAxkkOE83W2cOT7IWhFc9aPaaQmQDdgzuXCv+ppZHa++buSkN+                                                         
gg0tcr7Fw8NLGa5+Uzec2rEg0WmeevB13AIoYp0MZyETq46t+jk9puNwZwIt9XgB                                                         
ZufGtZEwWbFWw/vVLNwOXBe4UWStGRWzgPpEeSv5Tb1VjLZIBdGphTIK22Amz6Zb                                                         
ThMsiMnyJafEwJ/T8PQO3myS91vUHEuoOMAzoUID4kN0MEZ3+XahyK0HJVq68KsV                                                         
ObefXG1vvA3GAJ29kxJaqvRfgYnqZryWN7w3CHjNU4c/2Jkp+n8L0SnxaNA+WYA7                                                         
jiPyTF0is8uzMlYQ4l1Lzh/8/MpvhCQF8r22dwIDAQABAoIBAQC6dWBjhyEOzjeA                                                         
J3j/RWmap9M5zfJ/wb2bfidNpwbB8rsJ4sZIDZQ7XuIh4LfygoAQSS+bBw3RXvzE                                                         
pvJt3SmU8hIDuLsCjL1VnBY5pY7Bju8g8aR/3FyjyNAqx/TLfzlLYfOu7i9Jet67                                                         
xAh0tONG/u8FB5I3LAI2Vp6OviwvdWeC4nOxCthldpuPKNLA8rmMMVRTKQ+7T2VS                                                         
nXmwYckKUcUgzoVSpiNZaS0zUDypdpy2+tRH3MQa5kqN1YKjvF8RC47woOYCktsD                                                         
o3FFpGNFec9Taa3Msy+DfQQhHKZFKIL3bJDONtmrVvtYK40/yeU4aZ/HA2DQzwhe                                                         
ol1AfiEhAoGBAOnVjosBkm7sblK+n4IEwPxs8sOmhPnTDUy5WGrpSCrXOmsVIBUf                                                         
laL3ZGLx3xCIwtCnEucB9DvN2HZkupc/h6hTKUYLqXuyLD8njTrbRhLgbC9QrKrS                                                         
M1F2fSTxVqPtZDlDMwjNR04xHA/fKh8bXXyTMqOHNJTHHNhbh3McdURjAoGBANkU                                                         
1hqfnw7+aXncJ9bjysr1ZWbqOE5Nd8AFgfwaKuGTTVX2NsUQnCMWdOp+wFak40JH                                                         
PKWkJNdBG+ex0H9JNQsTK3X5PBMAS8AfX0GrKeuwKWA6erytVTqjOfLYcdp5+z9s                                                         
8DtVCxDuVsM+i4X8UqIGOlvGbtKEVokHPFXP1q/dAoGAcHg5YX7WEehCgCYTzpO+                                                         
xysX8ScM2qS6xuZ3MqUWAxUWkh7NGZvhe0sGy9iOdANzwKw7mUUFViaCMR/t54W1                                                         
GC83sOs3D7n5Mj8x3NdO8xFit7dT9a245TvaoYQ7KgmqpSg/ScKCw4c3eiLava+J                                                         
3btnJeSIU+8ZXq9XjPRpKwUCgYA7z6LiOQKxNeXH3qHXcnHok855maUj5fJNpPbY                                                         
iDkyZ8ySF8GlcFsky8Yw6fWCqfG3zDrohJ5l9JmEsBh7SadkwsZhvecQcS9t4vby                                                         
9/8X4jS0P8ibfcKS4nBP+dT81kkkg5Z5MohXBORA7VWx+ACohcDEkprsQ+w32xeD                                                         
qT1EvQKBgQDKm8ws2ByvSUVs9GjTilCajFqLJ0eVYzRPaY6f++Gv/UVfAPV4c+S0                                                         
kAWpXbv5tbkkzbS0eaLPTKgLzavXtQoTtKwrjpolHKIHUz6Wu+n4abfAIRFubOdN                                                         
/+aLoRQ0yBDRbdXMsZN/jvY44eM+xRLdRVyMmdPtP8belRi2E2aEzA==                                                                 
-----END RSA PRIVATE KEY-----                                                                                            
bandit13@bandit:~$ ssh -i sshkey.private -p 2220 bandit14@bandit.labs.overthewire.org
```
Now I am Connected using SSH key to bandit14 
