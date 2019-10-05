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

```python
def rearrange(A):
    for i in range(len(A)):
        A[i:i + 2] = sorted(A[i:i + 2], reverse=i % 2)
```
complexity: o(n), space: o(1)
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

7) Write a program which takes as input a sorted array and updates it so that all duplicates have been
removed and the remaining elements have been shifted left to fill the emptied indices. Return the
number of valid elements.

```python 
def remove_duplicates(A):
    for i in reversed(range(len(A))):
        if A[i] == A[i-1]:
            A.pop(i)
    return len(A)

```
complexity: o(n^2), space: o(1)
---------------
```python
def remove_duplicates(A):
    if not A:
        return 0
    write_index = 1
    for i, _ in enumerate(range(len(A))):
        if A[write_index - 1] != A[i]:
            A[write_index] = A[i]
            write_index += 1
    return write_index
```
complexity: o(n), space: o(1)
---------------

8) Implement a function which takes as input an array and a key, and updates the array so
that all occurrences of the input key have been removed and the remaining elements have been
shifted left to fill the emptied indices. Return the number of remaining elements. There are no
requirements as to the values stored beyond the last valid element.
 ```python
 def remove_element_occurances(A, key):
    write_index = 0
    for i, _ in enumerate(range(len(A))):
        if A[i] != key:
            A[write_index] = A[i]
            write_index += 1
    return write_index
 ```

complexity: o(n), space: o(1)
---------------

9) Write program that takes an array denoting the daily stock price, and retums the maximum profit
that could be made by buying and then selling one share of that stock. There is no need to buy if a no profit is possible.

```python
def max_profit(prices):
    max_profit, minimuni_price_so_far = 0,float('Inf')
    for price in prices:
        profit = price - minimuni_price_so_far
        max_profit = max(profit,max_profit)
        minimuni_price_so_far = min(price,minimuni_price_so_far)
    return max_profit

```
complexity: o(n), space: o(1)
---------------

10) Write a program that computes the maximum profit that can be made by buying and selling a share at most twice. The second buy must be made on another date after the first sale.
```python
def buy_and_sell_stock_twice(prices):
    max_total_profit, minimum_price_so_far = 0, float('inf')
    first_buy_sell_profits = [0] * len(prices)
    for i, price in enumerate(range(len(prices))):
        minimum_price_so_far = min(minimum_price_so_far, price)
        max_total_profit = max(max_total_profit, price - minimum_price_so_far)
        first_buy_sell_profits[i] = max_total_profit
    max_price_so_far = float('-inf')
    for i, price in reversed(list(enumerate(prices[1:], 1))):
        max_price_so_far = max(max_price_so_far, price)
        max_total_profit = max(max_total_profit, max_price_so_far - price + first_buy_sell_profits[i - 1])
    return max_total_profit

```
complexity: o(n), space: o(n)
---------------




