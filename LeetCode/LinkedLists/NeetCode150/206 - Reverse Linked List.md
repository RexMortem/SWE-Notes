https://leetcode.com/problems/reverse-linked-list/

> [!tip]- Hint 1
> Focus on just a single node in the middle of a linked list, and what you need to do to point the arrows in the right way. 

>[!tip]- Hint 2
>For any node, you'll have to set "next" to the node before. Use a variable to store the node before. 
>
>If you set "next" to the node before, what will you have to keep track of to keep iterating through the linked list?

> [!success]- Python Solution
> 
> ```Python
> class Solution:
>     def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
>         prev = None
>         
>         while head:
>             temp = head.next
>             head.next = prev
>             prev = head
>             head = temp
> 
>         return prev
> ```

