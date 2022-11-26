---
exclude: true
---
# Credstuff

[Cryptography](..)  

## Problem Description
Author: Will Hong / LT 'syreal' Jones  
Description  

We found a leak of a blackmarket website's login credentials. Can you find the password of the user cultiris and successfully decrypt it?  
Download the leak [here](https://artifacts.picoctf.net/c/534/leak.tar). The first user in usernames.txt corresponds to the first password in passwords.txt.  
The second user corresponds to the second password, and so on.  

## Write Up

The give file is compressed using tar, so to uncompress it run `tar xvf leak.tar` on a Linux machine, in the same directory the downloaded file is located.  
There are 2 files generated "passwords.txt" and "usernames.txt".  
Looking "usernames.txt" there are 505 lines of usernames. To find the user "cultiris" run `cat usernames.txt | grep "cultiris" -n`.  
This shows the user name is on line 378. To search the "passwords.txt" file run `sed -n 378p passwords.txt`. This searches for the 378th line of the "passwords.txt" file.  
After the command is ran, "cvpbPGS{P7e1S_54I35_71Z3}" is displayed. This is an encrypted version of the flag.  
The flag is encrypted with a ROT13 encryption scheme. Using the ROT13 recipe in [CyberChef](https://gchq.github.io/CyberChef/) the flag is decrypted.  

## Flag

picoCTF{C7r1F_54V35_71M3}  
