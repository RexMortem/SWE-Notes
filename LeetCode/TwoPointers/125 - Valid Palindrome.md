https://leetcode.com/problems/valid-palindrome/

>[!success]- Python Solution
> ```python
> class Solution:
>     def isPalindrome(self, s: str) -> bool:
>         s = "".join(filter(lambda x: x.isalnum(), s.upper()))
> 
>         for i in range(len(s)//2):
>             if s[i] != s[len(s) - i - 1]:
>                 return False
>         
>         return True
> ```