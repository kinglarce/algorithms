# Remove Nth Node From End of List

#### Links:

Remove Nth Node From End of List -[ ](https://leetcode.com/problems/maximum-subarray/)[https://leetcode.com/problems/remove-nth-node-from-end-of-list/](https://leetcode.com/problems/remove-nth-node-from-end-of-list/)

#### Problem:

Given the `head` of a linked list, remove the `nth` node from the end of the list and return its head.

**Example 1:**

![](https://assets.leetcode.com/uploads/2020/10/03/remove\_ex1.jpg)

```
Input: head = [1,2,3,4,5], n = 2
Output: [1,2,3,5]
```

#### Solutions

{% tabs %}
{% tab title="Two Passes - O(n)" %}
{% hint style="success" %}
Time: O(n), Space: O(1)
{% endhint %}

{% hint style="info" %}
**Hint:** Idea is to set a `slow` which holds the auxiliary head and `fast` pointer which serves as stopping pointer once we traverse into the linked list.&#x20;

Set the `fast` pointer head to the nth node from the end of the list because this will serve as a stoppage point later on.&#x20;

We use a dummy auxiliary head for `slow` pointer as this will handle the cases for removing only one node, removing the head and guaranteeing the `slow` pointer doesn't reach out of bounds.

Then finally, once traversal of the `fast` pointer is done, then just `slow.next` to `slow.next.next` which performs removal of the node and return the auxiliary head.
{% endhint %}

```python
def remove_nth_from_end(head: Optional[ListNode], n: int) -> Optional[ListNode]:
    dummy = ListNode(0, head)
    slow = dummy
    fast = head

    for _ in range(n):
        fast = fast.next

    while fast:
        slow = slow.next
        fast = fast.next

    slow.next = slow.next.next
    
    return dummy.next
```
{% endtab %}
{% endtabs %}
