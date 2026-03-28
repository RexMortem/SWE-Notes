https://leetcode.com/problems/longest-substring-without-repeating-characters/

>[!hint]- Hint
>The core idea is to maintain a window (represented by a left pointer and right pointer). 
>
>Move the right pointer forwards:
>- If you encounter a new character, then add it to the window's character set. 
>- If you encounter an old character, then shrink the window (by moving the left pointer) until the character no longer appears twice in the window.
>
>This covers the optimal solution because it covers all 
>
>This is also $O(2n) = O(n)$ rather than quadratic ($O(1 + 2 + \dots + n = \frac{n(n+1)}{2})$)

> [!success]- Python Solution
> ```python
> class Solution:
>     def lengthOfLongestSubstring(self, s: str) -> int:
>         l = 0
>         r = 0
>         mLength = 0
>         cChars = set()
> 
>         while (l <= r) and (r < len(s)):
>             # remove from cChars and update left pointer until none
>             while s[r] in cChars:
>                 cChars.remove(s[l])
>                 l += 1
>             
>             # update right pointer
>             cChars.add(s[r])
>             mLength = max(mLength, r - l + 1)
>             r += 1 
> 
>         return mLength
> ```