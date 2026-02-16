
> [!success]- Solution with typecasting
> ```python
> class Solution:
>     def isHappy(self, n: int) -> bool:
>         s = set()
>         
>         def step(n):
>             n = str(n)
>             tr = 0
> 
>             for sl in n:
>                 tr += int(sl)**2
> 
>             return tr
> 
>         while not (n in s):
>             s.add(n)
>             n = step(n)
> 
>             if n == 1:
>                 return True
> 
>         return False
> ```

> [!success]- Solution with maths
> ```python
> class Solution:
>     def isHappy(self, n: int) -> bool:
>         s = set()
>         
>         def step(n):
>             tr = 0
> 
>             while n > 0:
>                 unit = n % 10
>                 tr += unit**2
>                 n //= 10
>             
>             return tr
> 
>         while not (n in s):
>             s.add(n)
>             n = step(n)
> 
>             if n == 1:
>                 return True
> 
>         return False
> ```