The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed.
For this level it may be useful to create a directory under /tmp in which you can work using mkdir. For example: mkdir /tmp/myname123. 
Then copy the datafile using cp, and rename it using mv (read the manpages!)

```shell
SSH remote host (hostname or ip address): bandit.labs.overthewire.org                                                    
SSH remote port [22]: 2220                                                                                               
SSH remote username: bandit12                                                                                            
                                                                                                                         
bandit12@bandit.labs.overthewire.org's password:                                                                         
Welcome to Ubuntu 14.04 LTS (GNU/Linux 4.4.0-92-generic x86_64)                                                          
                                                                                                                         
 * Documentation:  https://help.ubuntu.com/                                                                              
                                                                                                                         
The programs included with the Ubuntu system are free software;                                                          
the exact distribution terms for each program are described in the                                                       
individual files in /usr/share/doc/*/copyright.                                                                          
                                                                                                                         
Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by                                                     
applicable law.                                                                                                          
                                                                                                                         
bandit12@bandit:~$ ls -la                                                                                                
total 28                                                                                                                 
drwxr-xr-x  3 bandit12 bandit12 4096 Oct 17 09:16 .
drwxr-xr-x 30 root     root     4096 Oct 17 09:16 ..
-rw-r--r--  1 bandit12 bandit12  220 Apr  9  2014 .bash_logout                                                           
-rw-r--r--  1 bandit12 bandit12 3637 Apr  9  2014 .bashrc                                                                
drwx------  2 bandit12 bandit12 4096 Oct 17 09:16 .cache
-rw-r--r--  1 bandit12 bandit12  675 Apr  9  2014 .profile                                                               
-rw-r-----  1 bandit13 bandit12 2546 Sep 28 14:04 data.txt                                                               
bandit12@bandit:~$ head data.txt                                                                                         
0000000: 1f8b 0808 5601 cd59 0203 6461 7461 322e  ....V..Y..data2.                                                       
0000010: 6269 6e00 013f 02c0 fd42 5a68 3931 4159  bin..?...BZh91AY                                                       
0000020: 2653 5914 13ca ff00 001b ffff faef 7fff  &SY.............                                                       
0000030: f9fb a79e de5b efbb ffff fd7f cf7b fbff  .....[.......{..                                                       
0000040: ff7f afbd 8ddb ff77 f752 ffff b001 3b56  .......w.R....;V                                                       
0000050: 6100 01a3 d400 0000 0068 d0d0 69a0 0000  a........h..i...                                                       
0000060: 007a 867a 9034 0340 6401 a340 0000 f280  .z.z.4.@d..@....                                                       
0000070: 01ea 0d1a 1a1a 0d01 9034 0e40 0000 0686  .........4.@....                                                       
0000080: 8d00 00c8 6819 3406 8d1e a003 d400 0c80  ....h.4.........                                                       
0000090: f534 0034 309a 0006 83d4 0000 01a6 80c8  .4.40...........
```
Lets See What can we do with this hex dump 

So I will be using tool called **xxd** it convert the hex dump back to its file and see what we can do next 

```shell
bandit12@bandit:~$ mkdir /tmp/microbot                                                                                   
bandit12@bandit:~$ cp data.txt /tmp/microbot                                                                             
bandit12@bandit:~$ cd /tmp/microbot          
bandit12@bandit:/tmp/microbot$ xxd -r data.txt > dump                                                                    
bandit12@bandit:/tmp/microbot$ file dump                                                                                 
dump: gzip compressed data, was "data2.bin", from Unix, last modified: Thu Sep 28 14:04:06 2017, max compression 
```
It Generated **gzip** file lets try to decompress it 

```shell
bandit12@bandit:/tmp/microbot$ gzip  -d dump                                                                             
gzip: dump: unknown suffix -- ignored         
```
I need to rename it and add extension *.gz*

NOTE Always use Help or man for any tool

```shell
bandit12@bandit:/tmp/microbot$mv dump dump.gz                                                                            
bandit12@bandit:/tmp/microbot$ gzip -d dump.gz                                                                           
bandit12@bandit:/tmp/microbot$ ls                                                                                        
bin.txt  data.txt  dump                                                                                                  
bandit12@bandit:/tmp/microbot$ file dump                                                                                 
dump: bzip2 compressed data, block size = 900k  
```
Now the Decompressed file is **bzip2** compressed file 

```shell
bandit12@bandit:/tmp/microbot$ mv dump.bzip dump.bzip2                                                                   
bandit12@bandit:/tmp/microbot$ bzip2 -d dump.bzip2                                                                       
bzip2: Can't guess original name for dump.bzip2 -- using dump.bzip2.out                                                  
bandit12@bandit:/tmp/microbot$ ls                                                                                        
bin.txt  data.txt  dump.bzip2.out                                                                                        
bandit12@bandit:/tmp/microbot$ file dump.bzip2.out                                                                       
dump.bzip2.out: gzip compressed data, was "data4.bin", from Unix, last modified: Thu Sep 28 14:04:06 2017, max compression 
```
Its compressed multiple times to lets try decompress all till we get the password

```shell
bandit12@bandit:/tmp/microbot$ mv data.gzip data.gz                                                                      
bandit12@bandit:/tmp/microbot$ gzip -d data.gz                                                                           
bandit12@bandit:/tmp/microbot$ ls                                                                                        
bin.txt  data  data.txt                                                                                                  
bandit12@bandit:/tmp/microbot$ file data                                                                                 
data: POSIX tar archive (GNU)                
bandit12@bandit:/tmp/microbot$ mv data data.tar                                                                          
bandit12@bandit:/tmp/microbot$ tar -xvf data.tar                                                                         
data5.bin                                                                                                                
bandit12@bandit:/tmp/microbot$ file data5.bin                                                                            
data5.bin: POSIX tar archive (GNU)                                                                                       
bandit12@bandit:/tmp/microbot$ mv data5.bin data.tar                                                                     
bandit12@bandit:/tmp/microbot$ tar -xvf data.tar                                                                         
data6.bin                                                                                                                
bandit12@bandit:/tmp/microbot$ mv data6.bin data.tar                                                                     
bandit12@bandit:/tmp/microbot$ tar -xvf data.tar                                                                         
data8.bin                                                                                                                
bandit12@bandit:/tmp/microbot$ file data8.bin                                                                            
data8.bin: gzip compressed data, was "data9.bin", from Unix, last modified: Thu Sep 28 14:04:06 2017, max compression 
bandit12@bandit:/tmp/microbot$ mv data8.bin data.gz                                                                      
bandit12@bandit:/tmp/microbot$ gzip -d data.gz                                                                           
bandit12@bandit:/tmp/microbot$ ls                                                                                        
bin.txt  data  data.tar  data.txt
bandit12@bandit:/tmp/microbot$ file data                                                                                 
data: ASCII text                                                                                                         
bandit12@bandit:/tmp/microbot$ cat data                                                                                  
The password is 8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL     
```
Bingo :D Level Solved
