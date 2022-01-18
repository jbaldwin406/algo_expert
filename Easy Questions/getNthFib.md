# Get Nth Fibonacci Number

### Problem Statement

The Fibonacci sequence is defined as follows: the first number of the sequence is 0, the second number is 1, and the nth number is the sum of the (n - 1)th and (n - 2)th numbers. Write a function that takes in an integer n and returns the nth Fibonacci number.

#

### Solution 1

```python
def getNthFib(n):
    fib = [0, 1]

    if n == 1:
        return 0

    for i in range(2, n):
        fib.append((fib[i - 1]) + (fib[i - 2]))

    return fib.pop()
```

### Alternate Solution

```python
def getNthFib(n):
    lastTwoNums = [0, 1]
    counter = 3

    while counter <= n:
        nextNum = lastTwoNums[0] + lastTwoNums[1]
        lastTwoNums[0] = lastTwoNums[1]
        lastTwoNums[1] = nextNum
        counter += 1

    if n > 1:
        return lastTwoNums[1]
    else:
        return lastTwoNums[0]
```