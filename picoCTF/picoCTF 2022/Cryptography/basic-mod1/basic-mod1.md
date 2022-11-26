---
exclude: true
---
# basic-mod1

[Cryptography](..)  

## Problem Description
Author: Will Hong  
Description  

We found this weird message being passed around on the servers, we think we have a working decryption scheme. Download the message [here](https://artifacts.picoctf.net/c/393/message.txt).  
Take each number mod 37 and map it to the following character set: 0-25 is the alphabet (uppercase), 26-35 are the decimal digits, and 36 is an underscore.  
Wrap your decrypted message in the picoCTF flag format (i.e. picoCTF{decrypted_message})

## Write Up

The encrypted message is "54 396 131 198 225 258 87 258 128 211 57 235 114 258 144 220 39 175 330 338 297 288". 
In the problem description they tell us how to decrypt the string, so you can decrypt this using any scripting language you like.  
Below is the Python Scrypt I made.

```
def basicMod1():
    enc_flag = (54,396,131,198,225,258,87,258,128,211,57,235,114,258,144,220,39,175,330,338,297,288)
    encoding = ('a','b','c','d','e','f','g','h','i','j','k','l','m','n','o','p','q','r','s','t','u','v','w','x','y','z','0','1','2','3','4','5','6','7','8','9','_')

    for i in range(len(enc_flag)):
        print(encoding[enc_flag[i]%37], end="")

basicMod1()
```

The script puts the encrpyted message in a tuple, as well as the encryption scheme.  
It then goes through each element of the encrypted message tuple. At each step it mods the element by 37, then finds the corresponding value from the encryption scheme.  

## Flag

picoCTF{r0und_n_r0und_79c18fb3}
