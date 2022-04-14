# Reverse Linked List

#### Links:

Reverse Linked List -[ ](https://leetcode.com/problems/maximum-subarray/)[https://leetcode.com/problems/reverse-linked-list/](https://leetcode.com/problems/reverse-linked-list/)

#### Problem:

Given the `head` of a singly linked list, reverse the list, and return _the reversed list_.

**Example 1:**

![](https://assets.leetcode.com/uploads/2021/02/19/rev1ex1.jpg)

```
Input: head = [1,2,3,4,5]
Output: [5,4,3,2,1]
```

#### Solutions

{% tabs %}
{% tab title="Iterative - O(n)" %}
{% hint style="success" %}
Time: O(n), Space: O(1)
{% endhint %}

{% hint style="info" %}
**Hint:** Create a `prev` node to keep the previous head/node.

Idea is to grab the `current.next` and assign to a temporary variable, assign the `current.next` to `prev` which would be initially a `null`, move the `prev` node to the `current` node and finally to move forward with the list, assign the `temp` to `current`.
{% endhint %}

```python
def reverse_list(head: Optional[ListNode]) -> Optional[ListNode]:
    if not head:
        return head
    
    current = head
    prev = None
    
    while current:
        temp = current.next
        current.next = prev
        prev = current
        current = temp
        
    return prev
```
{% endtab %}

{% tab title="Recursive - O(n)" %}
{% hint style="success" %}
Time: O(n), Space: O(n) - Space is O(n) because of call stack.
{% endhint %}

{% hint style="info" %}
**Hint:** Go through until you reach the point when the `head.next` is `null`, then return that head which is gonna be the previous head.

Once you got the `prev` head, assign the `current.next` node back to itself, and that's why its `current.next.next`.

e.g.&#x20;

h is `head`, p is `prev`\
1->2->3->4->5\
&#x20;                h   p \
1->2->3->4<-5\
&#x20;                h    p
{% endhint %}

```python
def reverse_list(head: ListNode) -> ListNode:
    if not head or not head.next:
        return head
    
    prev = self.reverseList(head.next)
    head.next.next = head
    head.next = None
    
    return prev
```
{% endtab %}
{% endtabs %}
