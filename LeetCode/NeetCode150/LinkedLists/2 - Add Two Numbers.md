https://leetcode.com/problems/add-two-numbers/description/

> [!success]- Python Solution (re-uses nodes, more complex)
> Would not recommend this solution since re-using the nodes introduces more complex logic. Easier to just create a new LinkedList for the solution.
> 
> ```python
> # save heads for returning at the end
> l1head = l1
> l2head = l2
> 
> # adding loop
> carry = 0
> 
> # caching for 
> l1prev = None
> l2prev = None
> 
> while l1 and l2:
> 	res = l1.val + l2.val + carry
> 
> 	if (res // 10) >= 1:
> 		carry = 1
> 	else:
> 		carry = 0
> 	
> 	l1.val = l2.val = (res % 10)
> 
> 	l1prev = l1
> 	l2prev = l2
> 
> 	l1 = l1.next
> 	l2 = l2.next
> 
> toCon = None
> toReturn = None
> 
> # caching
> toConPrev = None
> 
> if l1:
> 	toCon = l1
> 	toConPrev = l1prev
> 	toReturn = l1head
> else: # if both are terminated then l2 will be chosen arbitrarily here
> 	toCon = l2
> 	toConPrev = l2prev
> 	toReturn = l2head
> 
> while toCon and carry: 
> 	res = toCon.val + carry
> 
> 	if (res // 10) >= 1:
> 		carry = 1
> 	else:
> 		carry = 0
> 
> 	toCon.val = (res % 10)
> 	
> 	toConPrev = toCon
> 	toCon = toCon.next
> 
> if carry: # add a new node
> 	tail = ListNode(1)
> 	toConPrev.next = tail
> 
> return toReturn
> ```