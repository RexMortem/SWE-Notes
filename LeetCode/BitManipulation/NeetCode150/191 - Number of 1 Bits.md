https://leetcode.com/problems/number-of-1-bits

> [!success]- Python Solution by powers of 2 (slow)
> ```python
> class Solution:
>     def hammingWeight(self, n: int) -> int:
>         toret = 0
> 
>         x = 0
>         while (2**x) < n:
>             x += 1
> 
>         for i in range(x, -1, -1):
>             if n >= (2**i):
>                 n -= (2**i)
>                 toret += 1
> 
>                 if n == 0:
>                     break
>         
>         return toret
> ```

> [!success]- Python Solution by bitwise operators (less slow)
> We can make the previous solution way faster by replacing each appearance of `2**n` with `1<<n`.
> 
> In the loop, checking that the `ith` bit is 1 is explained in [[Bit Tricks#Setting, Clearing, Toggling, and Checking nth bit]].
> ```python
> class Solution:
>     def hammingWeight(self, n: int) -> int:
>         toret = 0
> 
>         x = 0
>         while (1 << x) < n:
>             x += 1
> 
>         for i in range(x, -1, -1):
>             if n & (1 << i):
>                 toret += 1
>         
>         return toret
> ```
> 
>This is fast but this is checking each bit from left-to-right; do we have a way of checking each bit from right-to-left which doesn't require us to check the size of the number first?

> [!success]- Python Solution by bitwise right-to-left
> We check the rightmost bit then use right-shifting to "consume" the rightmost bit to move onto the next rightmost bit.
> ```python
> class Solution:
>     def hammingWeight(self, n: int) -> int:
>         tr = 0
> 
>         while n:
>             if n & 1: # or equivalently, n % 2 == 1
>                 tr += 1
>             
>             n >>= 1
> 
>         return tr
> ```

> [!success]- Python Solution by clearing LSB magic (optimal)
> ```python
> class Solution:
>     def hammingWeight(self, n: int) -> int:
>         tr = 0
> 
>         while n:
>             n &= n-1
>             tr += 1
>         
>         return tr
> ```
> 
> See 