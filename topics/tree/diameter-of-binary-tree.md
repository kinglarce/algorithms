# Diameter of Binary Tree

#### Links:

Diameter of Binary Tree - [https://leetcode.com/problems/diameter-of-binary-tree/](https://leetcode.com/problems/diameter-of-binary-tree/)

#### Problem:

Given the `root` of a binary tree, return _the length of the **diameter** of the tree_.

The **diameter** of a binary tree is the **length** of the longest path between any two nodes in a tree. This path may or may not pass through the `root`.

The **length** of a path between two nodes is represented by the number of edges between them.

**Example 1:**

![](https://assets.leetcode.com/uploads/2021/03/06/diamtree.jpg)

```
Input: root = [1,2,3,4,5]
Output: 3
Explanation: 3 is the length of the path [4,2,1,3] or [5,2,1,3].
```

#### Solutions

{% tabs %}
{% tab title="DFS - O(n)" %}
{% hint style="success" %}
Time: O(n), Space: O(n)
{% endhint %}

{% hint style="info" %}
**Hint:** The idea follow the Max Depth of Binary Tree but flip side is to find the longest from the left to the right. \
There are 3 key points\
We do a bottom up approach where we go to the leaf of left and right node and once we reach there, then we set a default value of 0.\
Keep track of the longest path through the `longest` variable and do a Max Depth of each left and right node.

And once you got the max depth, now get the max again by comparing the current `longest` with the sum of both currently recorded of left and right node which is `depth_left` and `depth_right` .&#x20;
{% endhint %}

```python
def diameter_of_binary_tree(root: Optional[TreeNode]) -> int:
    _, diameter = max_depth(root, 0)
    return diameter

def max_depth(root, longest):
    if root is None:
        return 0, longest
    # Same as Max Depth of Binary Tree
    depth_left, longest = max_depth(root.left, longest)
    depth_right, longest = max_depth(root.right, longest)
    depth = max(depth_left, depth_right) + 1
    
    longest = max(longest, depth_left + depth_right)
    return depth, longest
```
{% endtab %}
{% endtabs %}
