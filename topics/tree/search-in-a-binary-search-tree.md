# Search in a Binary Search Tree

#### Links:

Search in a Binary Search Tree - [https://leetcode.com/problems/search-in-a-binary-search-tree/](https://leetcode.com/problems/search-in-a-binary-search-tree/)

#### Problem:

You are given the `root` of a binary search tree (BST) and an integer `val`.

Find the node in the BST that the node's value equals `val` and return the subtree rooted with that node. If such a node does not exist, return `null`.

**Example 1:**

![](https://assets.leetcode.com/uploads/2021/01/12/tree1.jpg)

```
Input: root = [4,2,7,1,3], val = 2
Output: [2,1,3]
```

#### Solutions

{% tabs %}
{% tab title="DFS - O(n)" %}
{% hint style="success" %}
Time: O(n), Space: O(n)
{% endhint %}

{% hint style="info" %}
**Hint:** BST rules is left is lower and right is greater than the current node value. So, just compare if `val` is lower than `root.val` then go left, otherwise, go right.
{% endhint %}

```python
def search_BST(root: Optional[TreeNode], val: int) -> Optional[TreeNode]:
    if not root:
        return root
    
    if val < root.val:
        return search_BST(root.left, val)
    elif val > root.val:
        return search_BST(root.right, val)
    else:
        return root
```
{% endtab %}
{% endtabs %}
