# Two Number Sum

### Problem Statement

Given an array of integers, no number in this array is repeated, and an integer representing the target sum, implement a function that finds whether there's a pair of numbers in the array that adds up to the target sum. Return the pair in an array. If such pair does not exist, return an empty array.

#

### Brute Force Approach
Iterate through the array with two for loops. At each integer in the first loop, stop and iterate with the other for loop through the rest of the array checking whether the two values equal the target sum.

### Solution
```python
def twoNumberSum(array, targetSum):
    for i in range(len(array) - 1):
        firstNum = array[i]

        for j in range(i + 1, len(array)):
            secondNum = array[j]

            if firstNum + secondNum == targetSum:
                return [firstNum, secondNum]

    return []
```

### Hash Table Approach

The problem can be solved by iterating through the array and at each integer check to see if there is another integer that is equal to the difference between the target sum and the current integer. Instead of using a nested for loop, we track the difference (targetSum - integer) in a hash table, which gives a constant time lookup on average. We will store the difference as the key, and at each iteration we check to see if the difference is in the hash table, if it is we return the (targetSum - integer), integer else we add the difference to the hash table. If no match is found and we've reached the end of the array, we return an empty array.

### Solution 
```python
def twoNumberSum(array, targetSum):
    sumMap = {}

    for num in array:
        if targetSum - num in sumMap:
            return [targetSum - num, num]
        else:
            sumMap[num] = True

    return []
```
