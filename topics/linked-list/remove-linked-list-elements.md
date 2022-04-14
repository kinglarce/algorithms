# Remove Linked List Elements

#### Links:

Remove Linked List Elements -[ ](https://leetcode.com/problems/maximum-subarray/)[https://leetcode.com/problems/remove-linked-list-elements/](https://leetcode.com/problems/remove-linked-list-elements/)

#### Problem:

Given the `head` of a linked list and an integer `val`, remove all the nodes of the linked list that has `Node.val == val`, and return _the new head_.

**Example 1:**

![](https://assets.leetcode.com/uploads/2021/03/06/removelinked-list.jpg)

```
Input: head = [1,2,6,3,4,5,6], val = 6
Output: [1,2,3,4,5]
```

#### Solutions

{% tabs %}
{% tab title="Pseudo Head - O(n)" %}
{% hint style="success" %}
Time: O(n), Space: O(1)
{% endhint %}

{% hint style="info" %}
**Hint:** Create a new auxiliary/pseudo head that points to `head` of linked list and if `current` node matches to targeted value, then skip the `current.next` and move it to `current.next.next`.

Why use a pseudo head? using a `prev` works fine of deleting something in the middle of the list(assuming you don't point your `prev` to the head) but this is good for dealing with deletion on the head of the linked list.
{% endhint %}

```python
def remove_elements(head: ListNode, val: int) -> ListNode:
    if not head:
        return
    
    dummy = ListNode(-1)
    dummy.next = head
    
    current = dummy
    while current.next: 
        if current.next.val == val:
            current.next = current.next.next
        else:
            current = current.next

    return dummy.next
```
{% endtab %}
{% endtabs %}
