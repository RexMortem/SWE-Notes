https://leetcode.com/problems/balanced-binary-tree/

Applications in AVL Trees.

**Height:** Length of longest path from a node to a leaf.

> [!success]- Python Solution
> ```python
> class Solution:
>     def isBalanced(self, root: Optional[TreeNode]) -> bool:
>         def explore(node: Optional[TreeNode]) -> (int, bool): # height, balanced
>             if not node:
>                 return (-1, True)
>             
>             lh,balanced = explore(node.left)
> 
>             if not balanced:
>                 return (0, False)
>             
>             rh, balanced = explore(node.right)
> 
>             if not balanced:
>                 return (0, False)
>             
>             hdiff = abs(lh - rh)
> 
>             if (hdiff <= 1):
>                 return (max(lh, rh) + 1, True)
>             else:
>                 return (0, False)
>             
>         return explore(root)[1]
> ```