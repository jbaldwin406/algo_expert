# Valid IP Addresses

### Problem Statement
You're given a string of length 12 or smaller, containing only digits. Write a function that returns all the possilbe IP addresses that can be created by inserting three .s in the string.
An IP address is a sequence of four positive integers that are separated by .s, where each individual integer is within the range 0 - 255 inclusive.
An IP address isn't valid if any of the individual integers contain leading 0s. 
Function should return the IP addresses in string format and in no particular order. If no valid IP addresses can be created from the string, function should return an empty list.

#

### Solution
```python
def isValid(ip):
    ip = ip.split('.')

    for i in ip:
        if len(i) > 3 or int(i) < 0 or int(i) > 255:
            return False

        if len(i) and int(i) == 0:
            return False

        if len(i) and int(i) != 0 and i[0] == '0':
            return False 

    return True


def validIPAddresses(string):
    sz = len(string)

    if sz > 12:
        return []

    snew = string
    result = []

    for i in range(1, sz - 2):
        for j in range(i + 1, sz - 1):
            for k in range(j + 1, sz):
                snew = snew[:k] + '.' + snew[k:]
                snew = snew[:j] + '.' + snew[j:]
                snew = snew[:i] + '.' + snew[i:]

                if isValid(snew):
                    result.append(snew)

                snew = string

    return result
```
