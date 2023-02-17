# Count Occurrences in Sorted Array


## Problem Statement

**Given a sorted array arr[] and a number x, write a function that counts the occurrences of x in arr[]. Expected time complexity is O(Logn)**

Examples: 

  Input: arr[] = {1, 1, 2, 2, 2, 2, 3,},   x = 2  
  Output: 4 // x (or 2) occurs 4 times in arr[]

  Input: arr[] = {1, 1, 2, 2, 2, 2, 3,},   x = 3  
  Output: 1 

  Input: arr[] = {1, 1, 2, 2, 2, 2, 3,},   x = 1  
  Output: 2 

  Input: arr[] = {1, 1, 2, 2, 2, 2, 3,},   x = 4  
  Output: -1 // 4 doesn't occur in arr[] 

## Algorithm
- Find First Occurrence and Last Occurrence indexes using binary search
- Return last - first +1, if element is not found return -1

## Code
```python

'''
 Time: O(logN)
 Space: O(1)
'''
    
    def count_occurrences(arr,N,x):

        first = first_occurrence(arr,N,x)
        
        if first == -1:
            return -1

        last = last_occurrence(arr,N,x)

        return (last-first)+1

```