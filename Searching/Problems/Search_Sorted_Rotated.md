# Search in a rotated sordted array
- [Search in a rotated sordted array](#search-in-a-rotated-sordted-array)
  - [Problem Statement](#problem-statement)
  - [Intuition](#intuition)
  - [Algorithm](#algorithm)
  - [Code](#code)

## Problem Statement
**Given a sorted and rotated array arr[] of size N and a key, the task is to find the key in the array or return -1.**

Example:  

Input  : arr[] = {5, 6, 7, 8, 9, 10, 1, 2, 3}, key = 3  
Output : Found at index 8

Input  : arr[] = {5, 6, 7, 8, 9, 10, 1, 2, 3}, key = 30  
Output : Not found

Input : arr[] = {30, 40, 50, 10, 20}, key = 10     
Output : Found at index 3

## Intuition
- For an optimial solution, we need to keep on halfing the array (logN)
- Its a fact that atleast one half of the array is definitely sorted.
- If we could just decide whether to skip this half or not for seaeching.

## Algorithm
- Move to mid element and find the sorted half (both halfs are sorted, we just need one)
  - For checking left half, if left most element is smaller than mid, it is sorted. For right half vice-versa
- Now, decide whether this half could contain target by comparing ranges
- If canot present, repeat whole process in this half, else move to next half
  
## Code 
```python

'''
  Time: O(logN) (Reducing size to half everytime)
  Space: 1
'''
  
  def search_rotated(arr,x):
    
    low, high = 0, len(arr)-1 
    
    while low<=high:
        
        mid = (low+high)//2
        
        if arr[mid]==x: return mid
        
        if arr[low] < arr[mid]:    # Checking If left half is sorted
            
            if arr[low]<= x < arr[mid]:   # checking if it can found in this left half
                high = mid-1
                
            else:
                low = mid+1    # moving to other half
                
        else:   # Right half is sorted
            
            if arr[mid] < x <= arr[high]:   # checking if it can found in this right half
                low = mid+1 
            else:
                high = mid-1  # moving to other half
                
    return -1
            
```