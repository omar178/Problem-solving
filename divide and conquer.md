1) The problem here is to find the max sub array from an array, the problem name is max sum subarray!
A video that illustrates the problem
## First Approach
Brute force simply iterate through diff array sizes then iterate through each element and calculate 
the sum and just return the max.

```python 
def max_sum_subarray(arr):
    maxi = float('-Inf')
    for poss_size in range(1, len(arr)):
        for start_idx in range(poss_size):
            if (start_idx + poss_size) > len(arr):
                break
            sum = 0
            for i in range(start_idx+poss_size):
                sum += arr[i]
            ans = max(maxi,sum)
    return ans


```
## Complexity: O(n^3)

Another approach is instead of adding l[i-1] --- l[i-n], we will only add the last element so if we are at index 0 will add value of index 1 and so on 
```python
def max_sum_another_app(arr)
    ans = float('-Inf')
    for start_idx in range(len(arr)):
        sum = 0
        for poss_size in range(1,len(arr))
            if start_idx+poss_size > len(arr):
                break
            sum += arr[start_idx+poss_size-1] #only add last element
            ans = max(ans,sum)
    return ans

```
## Complexity: O(n^2)

