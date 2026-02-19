
> [!success]- Solution
> ```python
> class Solution:
>     def spiralOrder(self, matrix: List[List[int]]) -> List[int]:
>         tr = [0] * (len(matrix)*len(matrix[0]))
>         m = len(matrix) # n of rows
>         n = len(matrix[0]) # n of columns
> 
>         i = 0
>         less = 0
> 
>         x = 0 
>         y = 0
> 
>         dx = 1
>         dy = 0
> 
>         while i < len(tr):
>             # need to switch dir
>             if (dx==1) and (x == (n-1-less)): # top-right corner
>                 dy = 1
>                 dx = 0
>             elif (dy==1) and (y == (m-1-less)): # bottom-right corner
>                 dx = -1
>                 dy = 0
>             elif (dx==-1) and (x == less): # bottom-left corner
>                 dy = -1
>                 dx = 0
>                 less += 1
>             elif (dy==-1) and (y == less): # top-left corner
>                 dy = 0
>                 dx = 1
> 
>             tr[i] = matrix[y][x]
>             i += 1
> 
>             x += dx
>             y += dy
> 
>         return tr
> ```