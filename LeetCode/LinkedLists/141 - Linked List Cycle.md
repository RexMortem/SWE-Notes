https://leetcode.com/problems/linked-list-cycle/description/

> [!success]- Python Solution (Easy)
> ```python
> class Solution:
>     def hasCycle(self, head: Optional[ListNode]) -> bool:
>         hs = set()
> 
>         while head:
>             if head in hs:
>                 return True
>             
>             hs.add(head)
>             head = head.next
> 
>         return False
> ```

> [!success]- Python Solution (Floyd's)
> ```python
> class Solution:
>     def hasCycle(self, head: Optional[ListNode]) -> bool:
>         p1 = head # fast pointer
>         p2 = head # slow pointer
> 
>         while p1 and p1.next:
>             p2 = p2.next
>             p1 = p1.next.next
> 
>             if p1 == p2:
>                 return True
>         
>         return False
> ```

> [!info]- Why does Floyd's work? (Intuition w/ informal proof)
> 
> If there isn't a cycle, the fast pointer will exit the list at some point.
> 
> If there is a cycle, we'll show that the fast pointer will lap the slow pointer. 
> 
> Eventually the slow pointer and the fast pointer will be in the cycle (of length $\lambda$) together. There is going to be some gap $\epsilon$ between the slow pointer and the fast pointer - specifically this gap will refer to the number of nodes the fast pointer needs to traverse to get to the slow pointer. Note $\epsilon < \lambda$ since the biggest gap in a cycle is one less than its length. 
> 
> If $\epsilon = 0$ then great! The slow pointer is at the same node at the fast pointer. 
> 
> If $\epsilon > 0$ then the next iteration will bring the fast pointer 2 steps forward and the slow pointer 1 step forward, reducing the number of nodes the fast pointer needs to traverse by 1 - therefore $\epsilon - 1$ is now the gap. So within $\lambda$ steps, we have that the fast pointer will catch the slow pointer. 
> 
> Interestingly, this shows it might not be possible for some cycles if the fast pointer moved 3 steps forward instead. 

> [!info]- Why does Floyd's work? (Proof)
> Let $x_{i}, x_{2i}$ be the slow and fast pointers respectively.
> 
> If a cycle is not present, then $x_{2i}$ will exit the linked list and not detect a cycle.
> 
> If a cycle is present, then Floyd's should detect the cycle: let the cycle be of length $\lambda$ and start at node $x_{j}$ (so we have $x_{j + \lambda} = x_{j}$ and more generally $x_{j + k\lambda} = x_{j} \; \forall k \in \mathbb{N}$).
> 
> We wish to show $\forall \lambda \geq 1, j \geq 0. \; \exists k, \alpha. \; (x_{j+\alpha} = x_{j + \alpha + k\lambda}) \land ((j + \alpha + k\lambda) = 2(j + \alpha))$ which means we have 2 nodes that are the same (because of cycle) and the index of one is double the index of the other - if these 2 nodes exist then we can say that the slow pointer and fast pointer will eventually collide. Note that $k$ here is the number of loops between the slow pointer and fast pointer and $\alpha$ is how far past the start point of the loop we are when we collide.
> 
> We can simplify $((j + \alpha + k\lambda) = 2(j + \alpha))$ to be $k\lambda = j + \alpha$ and thus $k\lambda - j = \alpha$. Now we can just choose sufficiently large $k$ that $k\lambda - j \geq 0$ and then let $\alpha = k\lambda - j$. If we want to find the first time the nodes collide, then we just find the smallest $k$ such that $k\lambda - j \geq 0$.