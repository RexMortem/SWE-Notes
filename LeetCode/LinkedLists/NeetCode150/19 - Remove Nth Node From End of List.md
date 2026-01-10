https://leetcode.com/problems/remove-nth-node-from-end-of-list/

> [!success]- Python Solution (Two Pass)
>```python
> class Solution:
>     def removeNthFromEnd(self, head: Optional[ListNode], n: int) -> Optional[ListNode]:
>         length = 0 
>         hp = head
> 
>         while hp:
>             hp = hp.next
>             length += 1
> 
>         prev = None
>         n = length - n 
>         hp = head
> 
>         while hp and (n > 0):
>             prev = hp
>             hp = hp.next
>             n -= 1
> 
>         lst = hp.next
> 
>         if prev:
>             prev.next = lst
>         else:
>             head = lst
> 
>         return head
> ```