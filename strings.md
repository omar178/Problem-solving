# Problem-solving
## Strings
1) Given a string containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.
An input string is valid if:
Open brackets must be closed by the same type of brackets.
Open brackets must be closed in the correct order.
Note that an empty string is also considered valid.
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
complexity: o(n) , space: o(1)
TestCases: "()[]{}" --> True, "([)]" --> False
------------------------------------------------------------------------------
