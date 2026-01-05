https://leetcode.com/problems/subsets

> [!success]- Python Solution (Iteration)
> ```python
> class Solution:
>     def subsets(self, nums: List[int]) -> List[List[int]]:
>         ps = [[]]
>         
>         for num in nums:
>             toAdd = []
> 
>             for ss in ps:
>                 nss = ss[:]
>                 nss.append(num)
>                 toAdd.append(nss)
>             
>             ps += toAdd
>         
>         return ps
> ```

Ed to-do:
- Understand the bitmask solution!!!
- Review backtracking