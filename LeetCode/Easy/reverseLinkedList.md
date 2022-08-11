# Reverse Linked List

>Given the head of a singly linked list, reverse the list, and return the reversed list.


-  Example 1:
![](../../../../../Pictures/rev1ex1.jpg)
Input: head = [1,2,3,4,5]
Output: [5,4,3,2,1]

- Example 2: 
![](../../../../../Pictures/rev1ex2.jpg)
Input: head = [1,2]
Output: [2,1]

- Example 3:
Input: head = []
Output: []



## 아이디어 

|                |아이디어1(Linked List)          |아이디어2(Stack) |아이디어3(Recursion)|
|----------------|-------------------------------|-----------------------------|-----------------------------|
|1 |이전(prev), 현재(curr),다음(next)를 유지 운영한다.|노드를 저장한 스택 생성 | 재귀 함수를 생성. 매개 변수로는 현재 노드와 이전 노드를 받음. 맨 처음 실행할 때 이전 노드가 존재하지 않기에 이전 노드를 받는 매개변수는 기본 매개변수로 만들고 None을 넣는다. |      
|2 |현재 노드가 None이 아닐 때까지 | 연결 리스트를 순회|base case를 작성. 현재 node가 None이라면 이전 노드를 리턴|
|  |`현재의 다음(next)을 임시 저장한다` |`스택에 현재 노드를 추가`||
|  |`현재의 다음(next)을 이전(prev)를 가리키도록 업데이트 한다.` |`마지막 노드는 넣지 않도록 한다.`||
|  |`이전(prev)를 현재 노드로 이동` |||
|  |`현재 노드를 임시 저장한 다음 노드로 이동한다.`            |||
|3 |  |스택의 모든 요소를 하나씩 꺼냄|recursive case를 작성|
| |  |`마지막 노드로부터 꺼내진 요소를 다음(next)으로 연결`|`현재 노드의 next 값을 변수에 담는다.`|
| |  ||`현재 노드의 next값에 이전 노드를 재할당 한다.`|
|4|  ||다음 노드 next(현재 노드의 next값)와 현재 노드를 인자로 넣어 재귀 호출을 한다.|
|시간 복잡도| O(N)|O(N)||
|공간 복잡도| O(1)|O(N), 스택에 모든 노드를 저장||



### 아이디어1(Linked List)  

```
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        prev= None
        curr=head
        
        while (curr!=None):
            next_temp= curr.next
            
            curr.next= prev
            prev= curr
            curr= next_temp
        return prev    
        
                       

```

### 아이디어2(Stack) 

```
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        if head == None:
            return head
        
        stack=[]
        
        curr = head
        
        while curr.next !=None:
            stack.append(curr)
            curr= curr.next
            
        first = curr
        
        while stack:
            curr.next = stack.pop()
            curr = curr.next
            
        curr.next = None
        
        return first

     

```

### 아이디어3(Recursion)
```
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def reverseList(self, head: ListNode) -> ListNode:
        def reverse(node: ListNode, prev: ListNode =None ):
            if not node:
                return prev
            
            next, node.next= node.next, prev
            return reverse(next,node)
        return reverse(head)
        

     

```