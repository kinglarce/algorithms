# Subtree of Another Tree

#### Links:

Subtree of Another Tree - [https://leetcode.com/problems/subtree-of-another-tree/](https://leetcode.com/problems/subtree-of-another-tree/)

#### Problem:

Given the roots of two binary trees `root` and `subRoot`, return `true` if there is a subtree of `root` with the same structure and node values of `subRoot` and `false` otherwise.

A subtree of a binary tree `tree` is a tree that consists of a node in `tree` and all of this node's descendants. The tree `tree` could also be considered as a subtree of itself.

**Example 1:**

![](https://assets.leetcode.com/uploads/2021/04/28/subtree1-tree.jpg)

```
Input: root = [3,4,5,1,2], subRoot = [4,1,2]
Output: true
```

#### Solutions

{% tabs %}
{% tab title="DFS - O(m * n)" %}
{% hint style="success" %}
Time: O(m \* n), Space: O(n) - `m` is `root`, `n` is `subRoot`
{% endhint %}

{% hint style="info" %}
**Hint:** Same idea as the "Same Tree" problem where we verified if both of the `p` and `q` trees are the same, but the before we do that is we need to find node in the `root` that is the same value of the parent node of `subRoot`

There are 2 key points

Find the value in the `root` that is the same as the `subRoot` parent value. If found, then check if it's the same tree and return results accordingly.

But if both, `left` and `right` return `False` value, then weren't able to find the `subRoot` in the `root` tree.
{% endhint %}

```python
def is_subtree(root: Optional[TreeNode], subRoot: Optional[TreeNode]) -> bool:
    if not root:
        return False
    if root.val == subRoot.val and is_same_tree(root, subRoot):
        return True
    left = is_subtree(root.left, subRoot)
    right = is_subtree(root.right, subRoot)
    return left or right
    
def is_same_tree(p, q):
    if p is None and q is None:
        return True
    if p is None or q is None:
        return False
    if p.val != q.val:
        return False
    
    left = self.isSameTree(p.left, q.left)
    right = self.isSameTree(p.right, q.right)
    
    return left and right
```
{% endtab %}
{% endtabs %}
