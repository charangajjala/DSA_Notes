# Quick Sort 
- [Quick Sort](#quick-sort)
  - [Partition of Quick Sort](#partition-of-quick-sort)
  - [Naive Partition](#naive-partition)
  - [Lomuto Partition](#lomuto-partition)
    - [Algorithm](#algorithm)
    - [Code](#code)
    - [Illustration](#illustration)
  - [Hoare Partition](#hoare-partition)
    - [Algorithm](#algorithm-1)
    - [Code](#code-1)
    - [Illustration](#illustration-1)

## Partition of Quick Sort
![](Assets/2023-03-01-12-01-02.png)
- Partition: The goal is to arrange elements in an array such that all elements less than or equal to a given pivot value comes before the pivot and all elements greater appear after the pivot.

## Naive Partition
- Idea is to create a temp array and on one traversal store elements <= pivot and second traversal store elements > pivot. 
- Copy the temp to given array
- This is **Stable**

```python
   '''
    Time: O(N)
    Space: O(N)
   '''
   def naive_partition(self, arr, l, h, p):
        temp = []
        index = 0
        for i in range(l, h+1):
            if arr[i] <= arr[p]:
                temp.append(arr[i])
        
        for i in range(l, h+1):
            if arr[i] > arr[p]:
                temp.append(arr[i])
                
        for i in range(l, h+1):
            arr[i] = temp[i-l]
```

## Lomuto Partition 
- This is **unstable**
### Algorithm
- We solve the problems asuming the pivot as always the last element
   - We mantian two virtual windows for pivot left and right elements
   - If element is <= pivot we extend the legt window by swaping it to the next postion of left window end, else move forward
   - Finally, swap the pivot to next postion of left window end
- If **pivot is not the last element**, we simply swap it with the last element.

### Code 
```python
   '''
   Time: O(N)
   Sopace: 1
   '''
   def lamuto_partition(arr, l, h):
        pivot = arr[h]
        i = l - 1
        for j in range(l, h):
            if arr[j] < pivot:
                i += 1
                arr[i], arr[j] = arr[j], arr[i]
        arr[i+1], arr[h] = arr[h], arr[i+1]
        return i+1

```
### Illustration
![](Assets/2023-03-01-13-05-16.png)

## Hoare Partition 
- The goal is to assume the pivot as the first element and finally return index j such that [l,j] are < intial pivot and [j+1,h] are >= intial pivot.
- This wont place the intial pivot at its right position
- But, this takes less swaps on average and works better than lomuto on average
- This is also **Unstable**
### Algorithm 
- The algorithm uses two indices, one starting at the beginning of the array (i) and the other starting at the end of the array (j).
-  It then moves the indices towards each other until they meet at an element that is on the wrong side of the partition. 
   - i.e. if **arr[i]> pivot and arr[j]< pivot** then swap them
-  The algorithm then swaps the elements and continues until the indices meet or cross, at which point it returns the index of the partition **(j)**.

### Code 
```python
   '''
    Time: O(N)
    Space: 1
   '''
def hoare_partition(arr, l, h):
    pivot = arr[l]
    i = l - 1
    j = h + 1
    while True:
        i += 1   # do while
        while arr[i] < pivot:
            i += 1

        j -= 1   # do while
        while arr[j] > pivot:
            j -= 1

        if i >= j:
            return j
        arr[i], arr[j] = arr[j], arr[i]

```
### Illustration 
![](Assets/2023-03-01-13-05-58.png)

