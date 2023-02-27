# Intersection of two Sorted Arrays

## Algorithm 
- Iterate in while loop till any of the one array is finished.
- In each iteration we look for smaller of the two elements from both the array and increase its pointer because it will not be in other list, hence not part of intersection.
- For intersection, if both the elements are equal we print it and increment both pointer only if it is not same as the last element printed in intersection.

## Code 
```python
   '''
   Time: O(n+m)
   Space: O(1)
   '''
   def intersection(a, b, n, m):

        i, j = 0, 0
        while i < n and j < m:
            if a[i] > b[j]:
                j += 1
            elif b[j] > a[i]:
                i += 1
            else:
                # when both are equal
                print(a[i], end=" ")
                i += 1
                j += 1

```

