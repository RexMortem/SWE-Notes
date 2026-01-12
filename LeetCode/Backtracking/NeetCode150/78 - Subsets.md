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

> [!success]- Python Solution (Backtracking)
> We have an iteration solution so backtracking seems unnecessary but it's important to build up that skill of generating backtracking solutions.
> 
> ```python
> class Solution:
>     def subsets(self, nums: List[int]) -> List[List[int]]:
>         ps = []
>         subset = [] # subset being built
> 
>         def dfs(i):
>             if i == len(nums): # reached a leaf of the decision tree
>                 ps.append(subset.copy())
>                 return
>             
>             # this is the backtracking part 
>             subset.append(nums[i])
>             dfs(i+1)
>             subset.pop()
>             dfs(i+1)
> 
>         dfs(0)
> 
>         return ps
> ```
> This backtracking solution makes a choice at each element of whether to include it or not - first, it explores all of the subsets which include the element and then it pops that element to backtrack and then explore all of the subsets which don't include the element. 
> 
> ```python
> # this is the backtracking part 
> dfs(i+1)
> subset.append(nums[i])
> dfs(i+1)
> subset.pop()
> ```
> 
> This is an alternate version of the backtracking part which first explores all of the subsets which don't include the element and then explore all of the subsets which do include the element. 
> 
> Note that you still need to pop the element to make sure that it's not kept in when you go to a higher recursive level and then descend to the element again (causing duplicate elements) - this is easier to visualise with a decision tree. 

> [!success]- Python Solution (Bitwise)
> Refer to [[Bit Tricks]] to understand the use of shifting here.
> 
> This solution works by having an intermediate representation which is a binary number where the `ith` digit of the binary number tells you whether the `ith` element of the array is included or not (1 if it is, 0 if not).
> 
> We can generate the numbers by just looping from 0 to $2^{n} - 1$. We use a bit trick to represent $2^{n}$ as an upper limit. 
> 
> We then convert each number to a subset by looping through the bits and adding an element if the bit is a 1, using a bit trick.
> ```python
> class Solution:
>     def subsets(self, nums: List[int]) -> List[List[int]]:
>         ps = []
>         
>         for nr in range(1 << len(nums)): # nr for numerical representation
>             ps.append([nums[i] for i in range(len(nums)) if ((1 << i) & nr) > 0])
>             
>         return ps
> ```