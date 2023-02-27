# Union of sorted arrays
- [Union of sorted arrays](#union-of-sorted-arrays)
  - [Problem Statement](#problem-statement)
  - [Algorithm](#algorithm)
  - [Code](#code)

## Problem Statement 
**Given two unsorted arrays that represent two sets (elements in every array are distinct), print the union  of two arrays in sorted order**

Example: 

arr1[] = {7, 1, 5, 2, 3, 6} 
arr2[] = {3, 8, 6, 20, 7} 
Then your program should print Union as {1, 2, 3, 5, 6, 7, 8, 20} in sorted order

## Algorithm 
- It is very similar to merger function in merger sort.
- Here, merger the sorted arrays but only process unique elements.
- We check for repeating elements and maintain sorted order based on if arr[i]>arr[j]
- Then print remaining elements in pending array.
  
## Code 
```python
class Solution:
    
    def mergeArrays(self,a,b,n,m):
        '''
        :param a: given sorted array a
        :param n: size of sorted array a
        :param b: given sorted array b
        :param m: size of sorted array b
        :return:  The union of both arrays as a list

        TIME: O(m+n)
        Spce: 1
        '''
        # code here 
        
        i=j=0
        temp =[]
        while(i<n and j<m):
            
            if i>0 and a[i]==a[i-1]:
                i+=1
                continue
            if j>0 and b[j]==b[j-1]:
                j+=1
                continue
            
            if a[i]<b[j]:
                print(a[i])
                i+=1
                
            elif b[j]<a[i]:
                print(b[j])
                j+=1
                
            else:
                print(a[i])
                i+=1
                j+=1
                
        while(i<n):
            if ((i>0 and a[i]!=a[i-1]) or i==0 ):
                print(a[i])
            i+=1
        while(j<m):
            if ((j>0 and b[j]!=b[j-1]) or j==0):
                print(b[j])
            j+=1
            
```