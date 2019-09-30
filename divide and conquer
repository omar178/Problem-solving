1) The problem here is to find the max sub array from an array, the problem name is max sum subarray!
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
