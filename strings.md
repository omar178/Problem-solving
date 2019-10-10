# Problem-solving
## Strings
1) https://leetcode.com/problems/valid-parentheses/</br>
Given a string containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.
```python
def isValid(s):
    
    if len(s) % 2 != 0:
        return False

    # Use list as a stack
    
    open_to_close = {'(':')', '{':'}', '[':']'}
    stack = []
    for bracket in s:
        if open_to_close.get(bracket,0) != 0:
            stack.append(bracket)
        else:
            stack_length = len(stack)
            if stack_length != 0:
                val = stack.pop(stack_length - 1)
                if open_to_close[val] == bracket:
                    continue
                else:
                    return False
                
    if len(stack) == 0:
        return True
    else:
        return False
            
  ```
### Complexity: O(n) , space: o(1)
### TestCases: "()[]{}" -> True, "([)]" -> False
------------------------------------------------------------------------------
2) https://leetcode.com/problems/first-unique-character-in-a-string/</br>
Given a string, find the first non-repeating character in it and return it's index. If it doesn't exist, return -1.
```python
def firstUniqChar(s):
    """
    :type s: str
    :rtype: int
    """
    # char_counter = {}

    # for ind,char in enumerate(s):
    #     if char_counter.get(char, -1) == -1:
    #         char_counter[char] = 1
    #     else:
    #         char_counter[char] += 1
    
    import collections
    char_counter = collections.Counter(s)
    
    for i in range(len(s)):
        if char_counter[s[i]] == 1:
            return i
         
    for ind,char in enumerate(s):
        if char_counter[char] == 1:
            return ind
        
    return -1
```
### Complexity: O(n), space: o(n)
### TestCases: s = "leetcode" -> 0, s = "loveleetcode" -> 2
------------------------------------------------------------------------------
3) https://leetcode.com/problems/valid-palindrome/</br>
Given a string, determine if it is a palindrome, considering only alphanumeric characters and ignoring cases.
```python
class Solution(object):
    def isPalindrome(self, s):
        """
        :type s: str
        :rtype: bool
        """
        if len(s) == 0:
            return True
        
        s = [letter.lower() for letter in s if letter.isalpha() or letter.isnumeric()]

        if len(s) == 1:
            return True

        else:
            
            last = -1
            for ind in range(len(s)//2):
                if s[ind] != s[last]:
                    return False
                last -= 1
                
            return True
```
### Complexity: O(n), space: o(1)
### TestCases: s = "A man, a plan, a canal: Panama" -> true, s = "race a car" -> false
------------------------------------------------------------------------------
4) https://leetcode.com/problems/implement-strstr/</br>
Return the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack.
```python
class Solution:
    def strStr(self, haystack: str, needle: str) -> int:
        
        if len(needle) == 0:
            return 0
        
        #if needle in haystack:
        #    return haystack.index(needle[0])
        #else:
        #    return -1
        
        for index, letter in enumerate(haystack):
            if len(needle)+index <= len(haystack):
                if needle == haystack[index:len(needle)+index]:
                    return index
                else:
                    continue
        return -1
```
### Complexity: O(n), space: o(1)
### TestCases: haystack = "hello", needle = "ll" -> 2
------------------------------------------------------------------------------
5) https://leetcode.com/problems/add-strings/</br>
Given two non-negative integers num1 and num2 represented as string, return the sum of num1 and num2.
```python
class Solution(object):
    def addStrings(self, num1, num2):
        """
        :type num1: str
        :type num2: str
        :rtype: str
        """
        return str(int(num1)+int(num2))
    
        g={"1":1,"2":2,"3":3,"4":4,"5":5,"6":6,"7":7,"8":8,"9":9,"0":0}
        
        def str_to_int(num,k,r):
            for i in range(len(num)-1,-1,-1):
                r+=g[num[i]]*k
                k*=10
            return(r)
        return str(str_to_int(num1,1,0)+str_to_int(num2,1,0))
```
### Complexity: O(len(num1) + len(num2)), space: o(1)
------------------------------------------------------------------------------
6) https://leetcode.com/problems/add-binary/</br>
Given two binary strings, return their sum (also a binary string).

```python
class Solution(object):
    def addBinary(self, a, b):
        """
        :type a: str
        :type b: str
        :rtype: str
        """
        return bin(int(a, 2) + int(b, 2))[2:]
    
        a_len = len(a)
        b_len = len(b)
        
        sum_in_decimal = 0
        sum_in_binary = ''
        
        for ind in range(len(a)):
            sum_in_decimal += (int(a[ind]) * (2 ** (a_len - 1 - ind)))
            
        for ind in range(len(b)):
            sum_in_decimal += (int(b[ind]) * (2 ** (b_len - 1 - ind)))
        
        if sum_in_decimal == 0:
            return '0'
        while sum_in_decimal > 0:
            sum_in_binary = str(sum_in_decimal % 2) + sum_in_binary
            sum_in_decimal /= 2
        
        return sum_in_binary
```
### Complexity: O(len(a) + len(b)), space: o(1)
------------------------------------------------------------------------------