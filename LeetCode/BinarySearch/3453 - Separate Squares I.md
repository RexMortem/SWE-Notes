https://leetcode.com/problems/separate-squares-i/

>[!warning]- Warning Hint 1
>Be very careful about it wanting you to find the **minimum** y-coordinate of a horizontal line; the area, with respect to the rising y-coordinate, forms a monotonic function BUT there may be multiple y-coordinate candidates if they all have exactly the same area below (think about if there's a large gap between two identical squares).
>
>So if you have multiple y-coordinate candidates, how do you ensure your binary search converges to the minimum one? You should think carefully about the relational operators (`<`,`>`, `<=`, `>=`). 

> [!solution]- Python Solution
> ```python
> class Solution:
>     def separateSquares(self, squares: List[List[int]]) -> float:
>         totalArea = 0
>         maxY = 0
>         minY = 0
> 
>         for x,y,l in squares:
>             totalArea += l*l
>             maxY = max(maxY, y+l)
>             minY = min(minY, y)
> 
>         def calculateArea(cy):
>             area = 0
> 
>             for x,y,l in squares:
>                 area += l * min(l, max(0, (y + l) - cy))
> 
>             return area
> 
>         l = minY
>         r = maxY
>         epsilon = 10**(-5)
>         cA = 0
>         target = totalArea/2
> 
>         while (r - l) > epsilon:
>             mid = (l + r)/2
>             val = calculateArea(mid)
> 
>             if val <= target: # undershoot: bring down y
>                 r = mid
>             else:
>                 l = mid
> 
>         return r
> ```