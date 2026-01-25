https://leetcode.com/problems/minimize-maximum-pair-sum-in-array/

> [!success]- Python Solution
> ```python
> class Solution:
>     def minPairSum(self, nums: List[int]) -> int:
>         nums.sort()
>         tr = 0
> 
>         for i in range(len(nums)):
>             j = len(nums) - i - 1
>             tr = max(tr, nums[i] + nums[j])
> 
>         return tr
> ```