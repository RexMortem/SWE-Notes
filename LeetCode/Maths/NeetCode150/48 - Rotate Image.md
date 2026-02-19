Idea for in-place: shuffle the integers 4 at a time. Then do this shuffling layer by layer. 

> [!success]- Solution via shuffling (layer by layer)
> ```python
> class Solution:
>     def rotate(self, matrix: List[List[int]]) -> None:
>         """
>         Do not return anything, modify matrix in-place instead.
> 
>         General formula: (x,y) -> (y, n - x)
> 
>         180 is: (y, n - x) -> (n - x, n - y)
>         90 counterclockwise is: (x, y) = (b, n - a)
>         x = b and y = n - a
>         b = x, a = n - y
>         (a, b) = (n - y, x)
> 
>         """
>         n = len(matrix)
>         m = n - 1
> 
>         for x in range((n+1)//2):
>             for y in range(x, n - x - 1):
>                 t = matrix[y][m - x] # 90 deg
>                 matrix[y][m - x] = matrix[x][y]
>                 
>                 t2 = matrix[m - x][m - y] # 180 deg
>                 matrix[m - x][m - y] = t
>                 
>                 t = matrix[m - y][x] # 270 deg i.e. 90 counter
>                 matrix[m - y][x] = t2
>                
>                 matrix[x][y] = t
>                 
>         return matrix
> ```