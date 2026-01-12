https://leetcode.com/problems/permutations

> [!success]- Python Solution
> ```python
> class Solution:
>     def permute(self, nums: List[int]) -> List[List[int]]:
>         tr = []
>         perm = []
>         rest = nums.copy()
> 
>         def dfs(i):
>             # dfs(i) represents having selected i elements already
>             if i == len(nums):
>                 tr.append(perm.copy())
>                 return
>             
>             for j in range(len(rest)):
>                 perm.append(rest[j])
>                 rest.pop(j)
>                 dfs(i+1)
>                 val = perm.pop()
>                 rest.insert(j, val)
>         
>         dfs(0)
>         return tr
> ```