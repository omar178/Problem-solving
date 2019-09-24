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



