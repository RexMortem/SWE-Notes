https://leetcode.com/problems/reorder-list/description/

> [!success]- Python Solution
> ```python
> class Solution:
>     def reorderList(self, head: Optional[ListNode]) -> None:
>         """
>         Do not return anything, modify head in-place instead.
>         """
>         fp = head.next
>         sp = head
> 
>         while fp and fp.next:
>             fp = fp.next.next
>             sp = sp.next
>         
>         h2 = sp.next # head of 2nd half linked list - let's reverse it now
>         sp.next = None # sever connection between lower and upper half of list
> 
>         prev = None
> 
>         while h2:
>             temp = h2.next
>             h2.next = prev
>             prev = h2
>             h2 = temp
> 
>         h2 = prev # now h2 is head of the reversed list
> 
>         # let's splice together head and h2 now
>         h1 = head
> 
>         while h2:
>             th1 = h1.next
>             th2 = h2.next
> 
>             h1.next = h2
>             h2.next = th1
> 
>             h1 = th1
>             h2 = th2
> 
>         return head
> ```