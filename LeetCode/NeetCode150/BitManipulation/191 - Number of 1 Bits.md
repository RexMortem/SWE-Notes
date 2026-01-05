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

> [!success]- Python Solution by bitwise operators (fast)
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
>             if n & (1 << i):
>                 toret += 1
>         
>         return toret
> ```