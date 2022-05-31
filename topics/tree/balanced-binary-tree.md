# Balanced Binary Tree

#### Links:

Balanced Binary Tree - [https://leetcode.com/problems/balanced-binary-tree/](https://leetcode.com/problems/balanced-binary-tree/)

#### Problem:

Given a binary tree, determine if it is height-balanced.

For this problem, a height-balanced binary tree is defined as:

> a binary tree in which the left and right subtrees of _every_ node differ in height by no more than 1.

**Example 1:**

![](https://assets.leetcode.com/uploads/2020/10/06/balance\_1.jpg)

```
Input: root = [3,9,20,null,null,15,7]
Output: true
```

**Example 2:**

![](https://assets.leetcode.com/uploads/2020/10/06/balance\_2.jpg)

```
Input: root = [1,2,2,3,3,null,null,4,4]
Output: false
```

#### Different Types of Trees

![Different Types of Binary Tree illustration&#x20;
https://towardsdatascience.com/5-types-of-binary-tree-with-cool-illustrations-9b335c430254](https://miro.medium.com/max/1400/1\*CMGFtehu01ZEBgzHG71sMg.png)

#### Solutions

{% tabs %}
{% tab title="DFS (Bottom Up)- O(n log n)" %}
{% hint style="success" %}
Time: O(n), Space: O(n)
{% endhint %}

{% hint style="info" %}
**Hint:** TODO
{% endhint %}

```python
def is_balanced_tree(root: Optional[TreeNode]) -> bool:
    is_balanced = True
    
    def max_depth(root):
        nonlocal is_balanced
        
        if not root:
            return 0

        depth_left = max_depth(root.left)
        depth_right = max_depth(root.right)

        if abs(depth_left - depth_right) > 1:
            is_balanced = False

        return max(depth_left, depth_right) + 1
    
    max_depth(root)
    return is_balanced
```
{% endtab %}

{% tab title="DFS (Top Down)- O(n log n)" %}
{% hint style="success" %}
Time: O(n log n), Space: O(n)
{% endhint %}

{% hint style="info" %}
**Hint:** TODO
{% endhint %}

```python
def is_balanced_tree(root: Optional[TreeNode]) -> bool:
    if not root:
        return True
    
    delta = max_depth(root.left) - max_depth(root.right)
    return abs(delta) < 2 \
        and is_balanced(root.left) \
        and is_balanced(root.right)

def max_depth(root: TreeNode):
    if not root:
        return 0
    
    left = max_depth(root.left)
    right = max_depth(root.right)
    
    return 1 + max(left, right)
```
{% endtab %}
{% endtabs %}
