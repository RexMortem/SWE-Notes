https://leetcode.com/problems/diameter-of-binary-tree/

>[!tip]- Hint 1
>Trees are acyclic.

> [!success]- Python Solution
> Note that technically I'm not using "depth" correctly here - I'm actually using `height` wherever depth is mentioned.
> 
> ```python
> class Solution:
>     def diameterOfBinaryTree(self, root: Optional[TreeNode]) -> int:
>         def explore(node: Optional[TreeNode]) -> (int, int): # (depth, diameter)
>             if not node:
>                 return (-1, 0)
>             
>             ld,ldia = explore(node.left)
>             rd,rdia = explore(node.right)
> 
>             cDepth = max(ld, rd) + 1
> 
>             return (cDepth, max(ldia, rdia, 2 + ld + rd))
> 
>         return explore(root)[1]
> ```