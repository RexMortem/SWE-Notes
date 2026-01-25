https://leetcode.com/problems/minimum-difference-between-highest-and-lowest-of-k-scores

> [!solution]- Python Solution
> ```python
> class Solution:
>     def minimumDifference(self, nums: List[int], k: int) -> int:
>         nums.sort()
> 
>         tr = nums[-1] - nums[0]
> 
>         for i in range(len(nums) - k + 1): # generate this from "j = i + k - 1" and knowing the "len(nums)" should be limit of j; "i = j - k + 1" and sub in j
>             j = i + k - 1
>             tr = min(tr, nums[j] - nums[i])
> 
>         return tr
> ```