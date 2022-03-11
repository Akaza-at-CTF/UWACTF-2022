# Substitutions

> Difficulty: Easy
>
> Author: AustinNguyen
>
> ROT13 is not the only substitution ciphers. Let's try some of the others.

Reverse the Vigenere and Casear process of encryption.

```python
from key import KEY
def caesar_dec(p,k):
    cipher = ""
    for i in range(len(p)):
        if p[i].isalpha():
            cipher += chr(((ord(p[i]) + 65 - len(k)) % 26) + 65)
        else:
            cipher += p[i]
    return cipher 

def vigenere_dec(p,k):
    cipher = ""
    for i in range(len(p)):
        if p[i].isalpha():
            cipher += chr((ord(p[i]) + 65 - ord(k[i % len(k)]) + 65) % 26 + 65) 
        else:
            cipher += p[i]
    return cipher
    
def main():
    cipher = vigenere_dec("LXS{EOPFUXG_HIEJHGF_PVH_NDV_HNHT}", key)
    flag = caesar_dec(cipher, KEY)

    f = open('flag.txt', 'w')
    f.write(flag)
    f.close()

if __name__ == '__main__':
    main()
```

The flag is `ISS{CLASSIC_CIPHERS_ARE_NOT_SAFE}`
