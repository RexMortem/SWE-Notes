https://leetcode.com/problems/minimum-absolute-difference

> [!success]- Python Solution
> ```python
> class Solution:
>     def minimumAbsDifference(self, arr: List[int]) -> List[List[int]]:
>         arr.sort()
> 
>         mAbs = arr[-1] - arr[0]
> 
>         for i in range(len(arr) - 1):
>             mAbs = min(mAbs, arr[i+1] - arr[i])
> 
>         tr = []
> 
>         for i in range(len(arr) - 1):
>             if arr[i+1] - arr[i] == mAbs:
>                 tr.append([arr[i], arr[i+1]])
> 
>         return tr
> ```