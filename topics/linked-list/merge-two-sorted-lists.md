# Merge Two Sorted Lists

#### Links:

Merge Two Sorted List -[ ](https://leetcode.com/problems/maximum-subarray/)[https://leetcode.com/problems/merge-two-sorted-lists/](https://leetcode.com/problems/merge-two-sorted-lists/)

#### Problem:

You are given the heads of two sorted linked lists `list1` and `list2`.

Merge the two lists in a one **sorted** list. The list should be made by splicing together the nodes of the first two lists.

Return _the head of the merged linked list_.

**Example 1:**

![](https://assets.leetcode.com/uploads/2020/10/03/merge\_ex1.jpg)

```
Input: list1 = [1,2,4], list2 = [1,3,4]
Output: [1,1,2,3,4,4]
```

#### Solutions

{% tabs %}
{% tab title="Iterative - O(m+n)" %}
{% hint style="success" %}
Time: O(m+n), Space: O(1)
{% endhint %}

{% hint style="info" %}
**Hint:** Create a new auxiliary linked list called `dummy` where the value between `list1` and `list2` will be compared which is lesser and then be placed on the new linked list.

Once the loop exits because one of the two linked lists doesn't have value anymore, then just append whichever linked list is that still has value to the tail of the auxiliary linked list called `dummy.`
{% endhint %}

```python
def merge_two_lists(list1: Optional[ListNode], list2: Optional[ListNode]) -> Optional[ListNode]:
    dummy = ListNode()
    current = dummy
    
    while list1 and list2:
        if list1.val < list2.val:
            current.next = list1
            list1 = list1.next
        else:
            current.next = list2
            list2 = list2.next
        current = current.next
    
    current.next = list1 or list2
        
    return dummy.next
```
{% endtab %}

{% tab title="Iterative - In Place - O(m+n)" %}
{% hint style="success" %}
Time: O(n), Space: O(1)
{% endhint %}

{% hint style="info" %}
**Hint:** Create a new head then set the next node to `list1`. The idea is with the help of the new head, we can compare both `list1` and `list2` value and then set the next node of the new head called `dummy` to which is lower between the two lists.

If `list1` if lower than `list2` then we don't touch it and just adjust the current node, otherwise, the formula is to get both the next node of `current` and `list2` and place it in a temporary variable then pointer the `current.next` to`list2`, then `list2.next` point to `list1` and then adjust the new of of `list2` and `list1` to the temporary head variable that has been saved earlier.

Once the loop exits because one of the two linked lists doesn't have value anymore, then just append whichever linked list is that still has value to the tail of the `current` and return the new `list1` head which is `dummy.next`.


{% endhint %}

```python
def merge_two_lists(self, list1: Optional[ListNode], list2: Optional[ListNode]) -> Optional[ListNode]:
    dummy = ListNode(0, list1)
    current = dummy
    
    while list1 and list2:
        if list1.val < list2.val:
            list1 = list1.next
        else:
            list1_next = current.next
            list2_next = list2.next
            current.next = list2
            list2.next = list1
            list2 = list2_next
            list1 = list1_next
        current= current.next
    
    current.next = list1 or list2
        
    return dummy.next
```
{% endtab %}
{% endtabs %}
