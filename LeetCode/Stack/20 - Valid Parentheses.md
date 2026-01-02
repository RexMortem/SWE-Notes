https://leetcode.com/problems/valid-parentheses/description/

> [!success]- Python Solution
> ```python
> class Solution:
>     def isValid(self, s: str) -> bool:
>         stack = []
> 
>         for c in s:
>             if c in ("(", "{", "["):
>                 stack.append(c)
>             else: # must be closing
>                 if not stack:
>                     return False
>                 
>                 # can use a HashMap instead to make this cleaner
>                 if (c == ")") and (stack[-1] == "("):
>                     stack.pop()
>                 elif (c == "}") and (stack[-1] == "{"):
>                     stack.pop()
>                 elif (c == "]") and (stack[-1] == "["):
>                     stack.pop()
>                 else:
>                     return False
> 
>         # if empty (not stack) -> valid because all opening brackets matched
>         return not stack
> ```