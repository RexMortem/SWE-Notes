https://leetcode.com/problems/maximum-depth-of-binary-tree/description/

> [!success]- Python Solution (Slightly Suboptimal)
> This is slightly suboptimal since having to access `mDepth` as a nonlocal (essentially global) variable is a cost that we can avoid.
> 
> Is there a way to write a solution that avoids keeping a global variable by returning something from `explore`?
> ```python
> class Solution:
>     def maxDepth(self, root: Optional[TreeNode]) -> int:
>         mDepth = 0
>         
>         def explore(node: Optional[TreeNode], cDepth):
>             if not node:
>                 return
>             
>             nonlocal mDepth
> 
>             mDepth = max(mDepth, cDepth)
>             explore(node.left, cDepth+1)
>             explore(node.right, cDepth+1)
>             
>         explore(root, 1)
> 
>         return mDepth
> ```

> [!success]- Python Solution (Optimal)
> ```python
> class Solution:
>     def maxDepth(self, root: Optional[TreeNode]) -> int:
>         if not root:
>             return 0
> 
>         return max(self.maxDepth(root.left), self.maxDepth(root.right)) + 1
> ```