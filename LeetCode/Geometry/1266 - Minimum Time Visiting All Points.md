https://leetcode.com/problems/minimum-time-visiting-all-points

> [!success]- Python Solution
> ```python
> class Solution:
>     def minTimeToVisitAllPoints(self, points: List[List[int]]) -> int:
>         lp = None
>         mt = 0
> 
>         for cp in points:
>             if not lp:
>                 lp = cp 
>                 continue
> 
>             # Chebyshev distance (2 formulations btw) - old one was min(diff[0], diff[1]) + abs(diff[0] - diff[1])
>             diff = (abs(cp[0] - lp[0]), abs(cp[1] - lp[1]))
>             mt += max(diff[0], diff[1])
> 
>             lp = cp
>         
>         return mt
> ```