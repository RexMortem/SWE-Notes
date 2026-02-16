
> [!success]- Solution
> ```python
> class Solution:
>     def plusOne(self, digits: List[int]) -> List[int]:
>         tc = 0
> 
>         for i in range(len(digits)-1, -1, -1):
>             digits[i] += 1
>             
>             if digits[i] == 10:
>                 digits[i] = 0
>                 tc = 1
>             else:
>                 tc = 0
>                 break
>         
>         if tc:
>             return [1] + digits
>         else:
>             return digits
> ```