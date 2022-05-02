# Maximum Depth of Binary Tree

#### Links:

Maximum Depth of Binary Tree - [https://leetcode.com/problems/maximum-depth-of-binary-tree/](https://leetcode.com/problems/maximum-depth-of-binary-tree/)

#### Problem:

Given the `root` of a binary tree, return _its maximum depth_.

A binary tree's **maximum depth** is the number of nodes along the longest path from the root node down to the farthest leaf node.

**Example 1:**

![](https://assets.leetcode.com/uploads/2020/11/26/tmp-tree.jpg)

```
Input: root = [3,9,20,null,null,15,7]
Output: 3
```

#### Solutions

{% tabs %}
{% tab title="DFS - O(n)" %}
{% hint style="success" %}
Time: O(n), Space: O(n)
{% endhint %}

{% hint style="info" %}
**Hint:**&#x20;
{% endhint %}

```python
def max_depth(root: Optional[TreeNode]) -> int:
    if not root:
        return 0

    left = self.maxDepth(root.left)
    right = self.maxDepth(root.right)
    
    return 1 + max(left, right)
```
{% endtab %}

{% tab title="BFS - O(n)" %}
{% hint style="success" %}
Time: O(n), Space: O(n)
{% endhint %}

{% hint style="info" %}
**Hint:**&#x20;
{% endhint %}

```python
def max_depth(self, root: Optional[TreeNode]) -> int:
    if not root:
        return 0
    
    queue = [root]
    count = 0
    
    while queue:
        
        for _ in range(len(queue)):
            node = queue.pop(0)
            
            if node.left:
                queue.append(node.left)
            
            if node.right:
                queue.append(node.right)
                
        count += 1
                
    return count
```
{% endtab %}
{% endtabs %}
