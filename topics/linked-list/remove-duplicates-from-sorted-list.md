# Remove Duplicates from Sorted List

#### Links:

Remove Duplicates from Sorted List -[ ](https://leetcode.com/problems/maximum-subarray/)[https://leetcode.com/problems/remove-duplicates-from-sorted-list/](https://leetcode.com/problems/remove-duplicates-from-sorted-list/)

#### Problem:

Given the `head` of a sorted linked list, _delete all duplicates such that each element appears only once_. Return _the linked list **sorted** as well_.

**Example 1:**

![](https://assets.leetcode.com/uploads/2021/01/04/list1.jpg)

```
Input: head = [1,1,2]
Output: [1,2]
```

#### Solutions

{% tabs %}
{% tab title="Iterative - O(n)" %}
{% hint style="success" %}
Time: O(n), Space: O(1)
{% endhint %}

{% hint style="info" %}
**Hint:** Iterate the list and check if `current.next` value is equal to `current` value, then just move forward the `current.next`. Also, check if `current.next` to prevent out of bounds.
{% endhint %}

```python
def delete_duplicates(head: Optional[ListNode]) -> Optional[ListNode]:
    current = head
    
    while current and current.next:
        if current.next.val == current.val:
            current.next = current.next.next
        else:
            current = current.next
            
    return head
```
{% endtab %}
{% endtabs %}
