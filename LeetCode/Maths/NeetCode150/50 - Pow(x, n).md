https://leetcode.com/problems/powx-n/description/

>[!warning]- Python Power Limitations
>Python's exponentation operator (`**`) can't handle massive numbers (it will lead to 'Numerical result out of range'), so you need to represent squaring as `x * x` rather than `x**2`.

> [!success]- Python Solution (Binary Exp)
> ```python
> class Solution:
>     def myPow(self, x: float, n: int) -> float:
>         def inner(x, n):
>             if (n == 0):
>                 return 1
>             
>             res = inner(x, n//2)
> 
>             if (n % 2) == 0:
>                 return res*res 
>             else:
>                 return x * res * res
> 
>         if n < 0:
>             return 1/inner(x, abs(n))
>         else:
>             return inner(x, abs(n))
> ```

