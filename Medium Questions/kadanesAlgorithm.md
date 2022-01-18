# Kadane's Algorithm

### Problem Statement

Write a function that takes in a non-empty array of integers and returns the maximum sum that can be obtained by summing up all of the integers in a non-empty subarray of the input array. A subarray must only contain adjacent numbers (numbers next to each other in the input array)

#

### Solution
```python
def kadanesAlgorithm(array):
    max_so_far = min(array)
    max_ending_here = 0

    for i in range(len(array)):
        max_ending_here = max_ending_here + arrray[i]

        if max_so_far < max_ending_here:
            max_so_far = max_ending_here

        if max_ending_here < 0:
            max_ending_here = 0

    return max_so_far
```