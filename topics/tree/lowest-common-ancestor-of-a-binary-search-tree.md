# Lowest Common Ancestor of a Binary Search Tree

#### Links:

Lowest Common Ancestor of a Binary Search Tree - [https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/)

#### Problem:

Given a binary search tree (BST), find the lowest common ancestor (LCA) of two given nodes in the BST.

According to the [definition of LCA on Wikipedia](https://en.wikipedia.org/wiki/Lowest\_common\_ancestor): “The lowest common ancestor is defined between two nodes `p` and `q` as the lowest node in `T` that has both `p` and `q` as descendants (where we allow **a node to be a descendant of itself**).”

**Example 1:**

![](https://assets.leetcode.com/uploads/2018/12/14/binarysearchtree\_improved.png)

```
Input: root = [6,2,8,0,4,7,9,null,null,3,5], p = 2, q = 8
Output: 6
Explanation: The LCA of nodes 2 and 8 is 6.
```

#### Solutions

{% tabs %}
{% tab title="DFS - O(n)" %}
{% hint style="success" %}
Time: O(n), Space: O(n)
{% endhint %}

{% hint style="info" %}
**Hint:** There's 2 key points to LCA \
If the current node itself is one of `p` or `q` , then one of them could possibly be an LCA when one returns `null` \
But, if at any point we found both `p` and `q` in the subtrees of `root`, then the LCA would be the parent that holds the subtrees of both `p` and `q`.
{% endhint %}

```python
def lowest_common_ancestor(root: 'TreeNode', p: 'TreeNode', q: 'TreeNode') -> 'TreeNode':
    if not root or root.val == p.val or root.val == q.val:
        return root
    
    left = lowestCommonAncestor(root.left, p, q)
    right = lowestCommonAncestor(root.right, p, q)
    
    if left and right:
        return root
    
    return left or right
```
{% endtab %}
{% endtabs %}
