# Caesar Cipher Encryptor

### Problem Statement
Given a non-empty string of lowercase letters and a non-negative integer representing a key, write a function that returns a new string obtained by shifting every letter in the input string by k positions in the alphabet, where k is the key.

Note that letters should "wrap" around the alphabet; in other words, the letter z shifted by one returns the letter a.

#

### Solution 1
```python
def caesarCipherEncryptor(string, key):
    e = ""
    
    for i in string:
        if i.islower():
            e += chr((ord(i) - 97 + key) % 26 + 97)
        elif i.isupper():
            e += chr((ord(i) - 65 + key) % 26 + 65)
        else:
            e += i

    return e
```

### Solution 2
```python
def caesarCipherEncryptor(string, key):
    newLetters = []
    newKey = key % 26
    alphabet = list("abcdefghijklmnopqrstuvwxyz")

    for letter in string:
        newLetters.append(getNewLetter(letter, newKey, alphabet))
    
    return "".join(newLetters)


def getNewLetter(letter, key, alphabet):
    newLetterCode = alphabet.index(letter) + key
    return alphabet[newLetterCode % 26]

```
