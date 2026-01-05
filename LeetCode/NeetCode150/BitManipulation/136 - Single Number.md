
> [!tip]- Hint 1: Solution with O(n) space 
> We can use a HashSet to create a fast (O(n)) solution but which has O(n) space. 
> There is a way to use bit manipulation to reduce to O(1) space.
> 
> ```python
> class Solution:
>     def singleNumber(self, nums: List[int]) -> int:
>         toret = 0
>         hs = set()
> 
>         for num in nums:
>             if num in hs:
>                 toret -= num
>             else:
>                 toret += num
>                 hs.add(num)
> 
>         return toret
> ```

>[!tip]- Hint 2
>What happens when two identical numbers are XORed together?
>Can this be extended to a running total variable i.e. if you have some variable X and then you XOR identical numbers onto X then does it do the same thing, even with different identical numbers inbetween?

>[!tip]- Hint 3
>When two identical numbers are XORed together, they cancel and become 0. Break it down into column by column analysis e.g. 5 against 5.
>
>101
>101
>======
>000
>
>When you have two 1s in the same column, they XOR to become 0.
>When you have two 0s in the same column, they XOR to become 0.
>---
>Let's consider the example of `[4, 1, 2, 1, 2]`:
>
>100
>001
>010
>001
>010
>
>So XORing all of these together should result in 4 remaining (since the two 1s cancel out and so do the two 2s). How does this work?
>
>Let's break it down column-by-column. In each column, we have a number of 1s. In the first, we have one 1. In the second, we have two 1s. In the third, we also have two 1s.
>
>Whenever we have an even number of 1s, they XOR to become 0. Whenever we have an odd number of 1s, they XOR to become 1. You can think of this as a light switch where each occurrence of 1 flips the switch.
>
>Each pair of repeating numbers will introduce either two 0s and two 1s into the column.
>
>So if the number that appears once has a 0 in this column, then the repeating numbers will introduce an even number of 1s and therefore the result will be a 0 in this column.
>
>If the number that appears once has a 1 in this column, then the repeating numbers will add an even number of 1s and since we have one 1 already, there will be an odd number of 1s and therefore the result will be a 1 in this column.

> [!success]- Python Solution
> ```python
> class Solution:
>     def singleNumber(self, nums: List[int]) -> int:
>         bm = 0
> 
>         for num in nums:
>             bm = bm ^ num
> 
>         return bm
> ```