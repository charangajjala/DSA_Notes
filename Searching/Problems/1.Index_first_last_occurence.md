- [Index of first Occurrence and last Occurrence in Sorted Array](#index-of-first-occurrence-and-last-occurrence-in-sorted-array)
  - [Problem Statement](#problem-statement)
  - [Algorithm](#algorithm)
  - [Code](#code)

# Index of first Occurrence and last Occurrence in Sorted Array

## Problem Statement 
**Given a sorted array arr[] with possibly duplicate elements, the task is to find indexes of the first and last occurrences of an element x in the given array.**

Examples: 

Input : arr[] = {1, 3, 5, 5, 5, 5, 67, 123, 125}, x = 5  
Output : First Occurrence = 2
         Last Occurrence = 5

Input : arr[] = {1, 3, 5, 5, 5, 5, 7, 123, 125 }, x = 7  
Output : First Occurrence = 6
              Last Occurrence = 6

## Algorithm
- Apply usaul binary search   
- 1st Occurence
  - When mid ==x, 
    - then check if it can be first occurrence -> If mid == 0 or arr[mid]!=arr[mid-1] return mid
    - Else check on the left half -> high = mid-1
- Last Occurence
  - When mid ==x, 
    - then check if it can be Last occurrence -> If mid == n-1 or arr[mid]!=arr[mid+1] return mid
    - Else check on the right half -> low = mid+1
  
## Code



```python
'''
 Time: O(logN)
 Space: O(1)
'''
def bsearch_first_last(arr,N,x):
    
    low = 0
    high = N-1
    first = None
    last = None

    # first occurrence
    while(low<=hig):
        
        mid = (low+high)//2
        
        if arr[mid] > x:
            high = mid-1
            
        elif arr[mid] <x:
            low = mid+1 
            
        else:
          if mid==0 or arr[mid] != arr[mid-1]:
              first = mid
          else:
              high = mid-1
              
    low = 0
    high = N-1

    # last occurrence
    while(low<=hig):
        low = 0
        high = N-1
        
        mid = (low+high)//2
        
        if arr[mid] > x:
            high = mid-1
            
        elif arr[mid] <x:
            low = mid+1 
            
        else:
          if mid==N-1 or arr[mid] != arr[mid+1]:
              last = mid
          else:
              low = mid+1
              
    if first is not None:
        return first,last
    else:
        return -1
        
            
```