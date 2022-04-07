# Invert Binary Tree

#### Links:

Invert Binary Tree - [https://leetcode.com/problems/invert-binary-tree/](https://leetcode.com/problems/invert-binary-tree/)

#### Problem:

Given the `root` of a binary tree, invert the tree, and return _its root_.

**Example 1:**

![](https://assets.leetcode.com/uploads/2021/03/14/invert1-tree.jpg)

```
Input: root = [4,2,7,1,3,6,9]
Output: [4,7,2,9,6,3,1]
```

#### Solutions

{% tabs %}
{% tab title="DFS - O(n)" %}
{% hint style="success" %}
Time: O(n), Space: O(n)
{% endhint %}

{% hint style="info" %}
**Hint:** Inverse `left` and `right` places from bottom to top as it pop off the call stack.
{% endhint %}

```python
def invertTree(root: Optional[TreeNode]) -> Optional[TreeNode]:
    if not root:
        return
    left = invertTree(root.left)
    right = invertTree(root.right)
    root.left = right
    root.right = left
    
    return root
```
{% endtab %}

{% tab title="BFS - O(n)" %}
{% hint style="success" %}
Time: O(n), Space: O(n)
{% endhint %}

{% hint style="info" %}
**Hint:** Inverse `left` and `right` from top to bottom.
{% endhint %}

```python
def invertTree(self, root):
    queue = [root]
    while queue:
        node = queue.pop(0)
        if node:
            node.left, node.right = node.right, node.left
            queue.append(node.left)
            queue.append(node.right)
    
    return root
```
{% endtab %}
{% endtabs %}
