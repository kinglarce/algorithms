# Validate Binary Search Tree

#### Links:

Validate Binary Search Tree - [https://leetcode.com/problems/validate-binary-search-tree/](https://leetcode.com/problems/validate-binary-search-tree/)

#### Problem:

Given the `root` of a binary tree, _determine if it is a valid binary search tree (BST)_.

A **valid BST** is defined as follows:

* The left subtree of a node contains only nodes with keys **less than** the node's key.
* The right subtree of a node contains only nodes with keys **greater than** the node's key.
* Both the left and right subtrees must also be binary search trees.

**Example 1:**

![](https://assets.leetcode.com/uploads/2020/12/01/tree1.jpg)

```
Input: root = [2,1,3]
Output: true
```

#### Solutions

{% tabs %}
{% tab title="DFS - O(n)" %}
{% hint style="success" %}
Time: O(n), Space: O(n)
{% endhint %}

{% hint style="info" %}
**Hint:** To validate it, node value should be compared with its lower and upper limit, and in this case `low` which is negative infinity and `high` which is positive infinity.

&#x20;As you go through left subtrees, `high` should be adjusted to the parents node value and for the right subtrees, `low` should be adjusted to parents node value.
{% endhint %}

```python
def is_valid_BST(root: TreeNode) -> bool:
    low = float('-inf')
    
    def inorder(root):
        if not root:
            return True
        if not inorder(root.left):
            return False
        if root.val <= low:
            return False
        low = root.val
        return inorder(root.right)
    
    return inorder(root)
```
{% endtab %}
{% endtabs %}
