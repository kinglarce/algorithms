# Binary Tree Inorder Traversal

#### Links:

Inorder Traversal - [https://leetcode.com/problems/binary-tree-inorder-traversal/](https://leetcode.com/problems/binary-tree-inorder-traversal/)

#### Problem:

Given the `root` of a binary tree, return _the inorder traversal of its nodes' values_.

**Example 1:**

```
Tree:
        1
          \ 
           2
          /  \ 
        3      4
Input: root = [1,null,2,3,4]
Output: [1,3,2,4]
```

#### Solutions

{% tabs %}
{% tab title="DFS - O(n)" %}
{% hint style="success" %}
Time: O(n), Space: O(n)
{% endhint %}

{% hint style="info" %}
**Hint:** \
DFS(Preorder) - Get current node then go left until it's empty then move to right.\
Pattern: Top -> Bottom -> Left -> Right -&#x20;

DFS(Inorder) - Go to very bottom left then get then move back to parent then move to right.\
Pattern: Bottom -> Left -> Top -> RIght

DFS(Postorder) - Go to very bottom of left and right then get and then move back to parent.\
Pattern: Bottom -> Top -> Left -> Right
{% endhint %}

```python
def inorder_traversal(root: Optional[TreeNode]) -> List[int]:
    result = []
    dfs(root, result)
    return result

def dfs(node, result):
    if not node:
        return
    dfs(node.left, result)
    result.append(node.val)
    dfs(node.right, result)
```
{% endtab %}
{% endtabs %}
