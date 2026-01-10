https://leetcode.com/problems/smallest-subtree-with-all-the-deepest-nodes/

> [!success]- Python Solution
> ```python
> # Definition for a binary tree node.
> # class TreeNode:
> #     def __init__(self, val=0, left=None, right=None):
> #         self.val = val
> #         self.left = left
> #         self.right = right
> class Solution:
>     def subtreeWithAllDeepest(self, root: Optional[TreeNode]) -> Optional[TreeNode]:
>         maxDepth = 0
>         nNodes = 0
> 
>         def explMaxDepth(node, depth):
>             if not node:
>                 return
>             
>             nonlocal maxDepth, nNodes
> 
>             if depth == maxDepth:
>                 nNodes += 1
>             elif depth > maxDepth:
>                 maxDepth = depth
>                 nNodes = 1
>             
>             explMaxDepth(node.left, depth+1)
>             explMaxDepth(node.right, depth+1)
>         
>         explMaxDepth(root, 0)
>         
>         # find those nodes and the common ancestor
> 
>         tr = None
> 
>         def explore(node, depth):
>             if not node:
>                 return 0
>             
>             count = 1 if depth == maxDepth else 0
> 
>             lval = explore(node.left, depth+1)
>             nonlocal tr
> 
>             if tr is not None:
>                 return
>             
>             rval = explore(node.right, depth+1)
> 
>             if tr is not None:
>                 return
>             
>             count += lval + rval
>             
>             if count == nNodes:
>                 tr = node
>             
>             return count
> 
>         explore(root, 0)
> 
>         return tr
> ```