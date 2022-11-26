---
exclude: true
---
# basic-mod2

[Cryptography](..)  

## Problem Description
AUTHOR: WILL HONG  
Description  

A new modular challenge!  
Download the message [here](https://artifacts.picoctf.net/c/499/message.txt).  
Take each number mod 41 and find the modular inverse for the result.  
Then map to the following character set: 1-26 are the alphabet, 27-36 are the decimal digits, and 37 is an underscore.  
Wrap your decrypted message in the picoCTF flag format (i.e. picoCTF{decrypted_message})  

## Write Up

The encrypted message is "268 413 110 190 426 419 108 229 310 379 323 373 385 236 92 96 169 321 284 185 154 137 186".  
This problem is nearly identical to "basic-mod1", but it is 1 indexed instead of 0 indexed, it uses mod 41 instead of 37, and there is a modular inverse.  
In the problem description they tell us how to decrypt the string, so you can decrypt this using any scripting language you like.  
Below is the Python script I made**.  

```
def modInverse(a, m):
    for x in range(1, m):
        if (((a%m) * (x%m)) %m == 1):
            return x
    return -1

def basicMod2():
    enc_flag = (268,413,110,190,426,419,108,229,310,379,323,373,385,236,92,96,169,321,284,185,154,137,186)
    encoding = ('a','b','c','d','e','f','g','h','i','j','k','l','m','n','o','p','q','r','s','t','u','v','w','x','y','z','0','1','2','3','4','5','6','7','8','9','_')

    for i in range(len(enc_flag)):
        print(encoding[modInverse(enc_flag[i] % 41,41)-1], end="")

basicMod2()
```

The script puts the encrpyted message in a tuple, as well as the encryption scheme.  
It then goes through each element of the encrypted message tuple.  
At each step it mods the element by 41, then passes the value to the `modInverse()` function.  
This function works by trying all numeric possibilities to find the modular inverse.  
It then subtracts 1 from the returned result, this is the index of the correct value.  

## Flag

picoCTF{1nv3r53ly_h4rd_c680bdc1}  

**The `modInverse()` function is from https://www.geeksforgeeks.org/multiplicative-inverse-under-modulo-m/ I did not make it myself, it is their code.  
