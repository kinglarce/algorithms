# Linked List Cycle

#### Links:

Linked List Cycle -[ ](https://leetcode.com/problems/maximum-subarray/)[https://leetcode.com/problems/linked-list-cycle/](https://leetcode.com/problems/linked-list-cycle/)

#### Problem:

Given `head`, the head of a linked list, determine if the linked list has a cycle in it.

There is a cycle in a linked list if there is some node in the list that can be reached again by continuously following the `next` pointer. Internally, `pos` is used to denote the index of the node that tail's `next` pointer is connected to. **Note that `pos` is not passed as a parameter**.

Return `true` _if there is a cycle in the linked list_. Otherwise, return `false`.

&#x20;

**Example 1:**

![](https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist.png)

```
Input: head = [3,2,0,-4], pos = 1
Output: true
Explanation: There is a cycle in the linked list, where the tail connects to the 1st node (0-indexed).
```

#### Solutions

{% tabs %}
{% tab title="Hashmap - O(n)" %}
{% hint style="success" %}
Time: O(n), Space: O(n)
{% endhint %}

{% hint style="info" %}
**Hint:** Keep track of the nodes that have been seen.
{% endhint %}

```python
def hasCycle(head: ListNode) -> bool:
    seen = set()
    while head is not None:
        if head in seen :
            return True
        seen .add(head)
        head = head.next
    return False
```
{% endtab %}

{% tab title="Two Pointer - O(n)" %}
{% hint style="success" %}
Time: O(n), Space: O(n)
{% endhint %}

{% hint style="info" %}
**Hint:** This uses Floyd Cycle algorithm which one is a slow runner, and one is a fast runner.

Two pointer approach, slow runner starts at the head and fast starts on the next node, and then fast pointer hops twice. If fast pointer or the next of it becomes `null` , then it means it doesn't have a cycle.
{% endhint %}

```python
def hasCycle(head: Optional[ListNode]) -> bool:
    if not head:
        return

    slow = head
    fast = head.next
    
    while slow:
        if not fast or not fast.next:
            break
        
        if slow == fast:
            return True
        
        slow = slow.next
        fast = fast.next.next
        
    return False
```
{% endtab %}
{% endtabs %}
