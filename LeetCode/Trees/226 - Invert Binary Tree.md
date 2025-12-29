https://leetcode.com/problems/invert-binary-tree/description/

> [!success]- Python Solution
> ```python
> class Solution:
>     def invertTree(self, root: Optional[TreeNode]) -> Optional[TreeNode]:
>         if root:
>             # flip children
>             temp = root.left
>             root.left = root.right
>             root.right = temp
> 
>             # invert children too
>             self.invertTree(root.left)
>             self.invertTree(root.right)
> 
>             return root
> ```