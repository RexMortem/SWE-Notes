https://leetcode.com/problems/same-tree/description/

>[!tip]- Hint
>A tree A is the same as a tree B if their root's values are the same and their left subtrees and right subtrees are equivalent. 

>[!warning]- Optimisation
>You should do the check of the root's values being the same before you do the check of the trees having matching subtrees since checking values is much cheaper than a potentially very deep recursive check.

> [!success]- Python Solution
> ```python
> class Solution:
>     def isSameTree(self, p: Optional[TreeNode], q: Optional[TreeNode]) -> bool:
>         if not p:
>             if not q:
>                 return True
>             else:
>                 return False
>         elif not q:
>             return False
>         
>         return (p.val == q.val) and self.isSameTree(p.left, q.left) and self.isSameTree(p.right, q.right)
> ```