https://leetcode.com/problems/subtree-of-another-tree/

>[!tip]- Hint
>A tree A is the *same* as another tree B if its root values are the same and A's left/right subtrees are the same as B's left/right subtree.
>
>A tree A is a subtree of another tree B if A is the same as any tree rooted by a node in B.

> [!success]- Python Solution
> 
> ```python
> class Solution:
>     def isSubtree(self, root: Optional[TreeNode], subRoot: Optional[TreeNode]) -> bool:
>         def isSame(A: Optional[TreeNode], B: Optional[TreeNode]):
>             if not A:
>                 return not B
>             elif not B:
>                 return False
>             
>             return (A.val == B.val) and isSame(A.left, B.left) and isSame(A.right, B.right)
> 
>         if not root:
>             return False
> 
>         # subroot constrained to at least 1 node so don't handle trivial case
> 
>         # check if subRoot is rooted at this spot
>         if (root.val == subRoot.val) and isSame(root, subRoot):
>             return True
>         
>         # now to check if children of root contain the subRoot
>         if self.isSubtree(root.left, subRoot):
>             return True
>         
>         if self.isSubtree(root.right, subRoot):
>             return True
>         
>         return False
> ```