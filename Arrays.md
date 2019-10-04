# Problem-solving
## Arrays
1) Implement a function which takes as input an array and a key, and updates the array so
that all occurrences of the input key have been removed and the remaining elements have been
shifted left to fill the emptied indices. Return the number of remaining elements. There are no
requirements as to the values stored beyond the last valid element.
```python
def delete_key(A, key):  # [2,1,2,3],[1,1,2,3]
    c = 0
    for i in range(len(A)):
        if A[i] == key:
            A[i] = A[i + 1]
            c += 1
    return len(A) - c
  ```
  complexity: o(n) , space: o(1)
  ------------------------------------------------------------------------------

  2) Write a program which takes as input a sorted atay A of integers and a positiveinteger m,
and updates A so that if x appears z times in A it appears exactly mn(Z,m) times in A. The update
to A should be performed in one pass, and no additional storage may be allocated.
```python
def max_m(A, m): # [2, 2, 2, 2]
    c = 0
    for i in range(len(A)):
        if c == 2 and A[i] == m:
            A[i] = 0

        if A[i] == m:
            c += 1
    return A
  ```
complexity: o(n), space: o(1)
------------------------------------------------------------------------------
3) Write a program which takes as input a sorted array and updates it so that all duplicates have been
removed and the remaining elements have been shifted left to fill the emptied indices. Return the
number of valid elements. Many languages have library functions for performing this operation-
you cannot use these functions.
```python
def delete_duplicate(A):
    if not A:
        return 0
    write_index = 1  # [2,3,5,7,7,11,11,11,13]
    for i in range(1, len(A)):
        if A[write_index - 1] != A[i]:
            write_index += 1
            A[write_index] = A[i]
    return write_index
  ```
complexity: o(n), space: o(1)
--------
4) Write a program that takes an array A of n numbers, and rearranges A's elements to get a new array having the property that B[0] < B[1] >Bl2, < B[3] > B[4]< B[5] >....
```python
def rearrange(A):
    A.sort()
    for i in range(1, len(A),2):
        A[i], A[i + 1] = A[i+1] , A[i]
    return A
```
complexity: o(nlogn), space: o(1)
-------------------

5) Write a program which takes as input two strings s and f of bits encoding binary numbers hon return list of s+f
```python
def plus_binary(s1, s2):
    sum = []
    carry = 0
    result = 0
    for i in reversed(range(0, len(s2))):
        result = carry + s1[i] + s2[i]
        if result == 2:
            sum.insert(i, 0)
            carry = 1
        elif result == 3:
            sum.insert(i, 1)
            carry = 1
        else:
            sum.insert(i, result)
        if i == 0:
            sum.insert(0, carry)
    return sum

```
complexity: o(n), space: o(n)
-------------------
6) Write a program which takes an array of n integers, where A[i] denotes the maximum you can advance from index l, and retums whether it is possible to advance to the last index starting from
the beginning of the array.
```python
def can_reach_end(A):
    i, furthest_reach_so_far, last_index = 0, 0, len(A) - 1
    while furthest_reach_so_far < last_index and i < last_index:
        furthest_reach_so_far = max(furthest_reach_so_far,A[i] + i)
        i += 1
    return furthest_reach_so_far >= last_index

```
complexity: o(n), space: o(1)
---------------

