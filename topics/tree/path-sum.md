# Path Sum

#### Links:

Invert Binary Tree - [https://leetcode.com/problems/invert-binary-tree/](https://leetcode.com/problems/invert-binary-tree/)

#### Problem:

Given the `root` of a binary tree and an integer `targetSum`, return `true` if the tree has a **root-to-leaf** path such that adding up all the values along the path equals `targetSum`.

A **leaf** is a node with no children.

**Example 1:**

![](https://assets.leetcode.com/uploads/2021/01/18/pathsum1.jpg)

```
Input: root = [5,4,8,11,null,13,4,7,2,null,null,null,1], targetSum = 22
Output: true
Explanation: The root-to-leaf path with the target sum is shown.
```

#### Solutions

{% tabs %}
{% tab title="DFS - O(n)" %}
{% hint style="success" %}
Time: O(n), Space: O(n)
{% endhint %}

{% hint style="info" %}
**Hint:** Reduce `targetSum` for each current node value and check if the node is already the leaf node as well as check if `targetSum` is already `0.`
{% endhint %}

```python
def has_path_sum(root: Optional[TreeNode], targetSum: int) -> bool:
    if not root:
        return False
    
    target_sum -= root.val
    if not root.left and not root.right:
        return target_sum == 0
    
    return has_path_sum(root.left, target_sum) or has_path_sum(root.right, target_sum)
```
{% endtab %}
{% endtabs %}
