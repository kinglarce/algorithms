# Same Tree

#### Links:

Same Tree - [https://leetcode.com/problems/same-tree/](https://leetcode.com/problems/same-tree/)

#### Problem:

Given the roots of two binary trees `p` and `q`, write a function to check if they are the same or not.

Two binary trees are considered the same if they are structurally identical, and the nodes have the same value.

**Example 1:**

![](https://assets.leetcode.com/uploads/2020/12/20/ex1.jpg)

```
Input: p = [1,2,3], q = [1,2,3]
Output: true
```

**Example 2:**

![](https://assets.leetcode.com/uploads/2020/12/20/ex2.jpg)

```
Input: p = [1,2], q = [1,null,2]
Output: false
```

#### Solutions

{% tabs %}
{% tab title="DFS - O(n)" %}
{% hint style="success" %}
Time: O(n), Space: O(n)
{% endhint %}

{% hint style="info" %}
**Hint:** There are 3 key points for verifying the tree

If both `p` and `q` value is the same and we reach to the end of each of their nodes, then True

If only one of both only reach the node or their value doesn't match to reach other, then False

Finally, if both `left` and `right` of both `p` and `q` is True, then its the same tree.
{% endhint %}

```python
def is_same_tree(p: Optional[TreeNode], q: Optional[TreeNode]) -> bool:
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
