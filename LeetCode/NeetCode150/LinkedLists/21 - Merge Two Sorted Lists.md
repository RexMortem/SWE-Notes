https://leetcode.com/problems/merge-two-sorted-lists/

>[!tip]- Hint: roots and nulls
>Writing the code that will iterate through the two linked lists will probably rely on having a non-null current node.
>
>You can either find this current node at the start (finding a root) or you can create a dummy root node which doesn't represent anything but points to the start of the merged list.
>
>The solution below presents a root-finding solution.

> [!success]- Python Solution
> ```python
> class Solution:
>     def mergeTwoLists(self, list1: Optional[ListNode], list2: Optional[ListNode]) -> Optional[ListNode]:
>         # this code is split into two tasks: finding the root and iterating through
>         root = None
>         cHead = None
> 
>         # root-finding logic could be shortened but at the expense of being more complex
>         if list1 and list2:
>             if list1.val < list2.val:
>                 root = list1
>                 list1 = list1.next
>             else:
>                 root = list2
>                 list2 = list2.next
>         elif list1:
>             root = list1
>             list1 = list1.next
>         elif list2:
>             root = list2
>             list2 = list2.next
>         else:
>             return None
> 
>         cHead = root
> 
>         # once we have a root, we can assume cHead is non-null for the iterating part
>         while list1 and list2:
>             if list1.val < list2.val:
>                 cHead.next = list1
>                 list1 = list1.next
>             else:
>                 cHead.next = list2
>                 list2 = list2.next
> 
>             cHead = cHead.next
> 
>         if list1:
>             cHead.next = list1
> 
>         if list2:
>             cHead.next = list2
> 
>         return root
> ```