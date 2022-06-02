# Two Sum IV - Input is a BST

#### Links:

Two Sum IV - Input is a BST - [https://leetcode.com/problems/two-sum-iv-input-is-a-bst/](https://leetcode.com/problems/two-sum-iv-input-is-a-bst/)

#### Problem:

Given the `root` of a Binary Search Tree and a target number `k`, return _`true` if there exist two elements in the BST such that their sum is equal to the given target_.

**Example 1:**

![](https://assets.leetcode.com/uploads/2020/09/21/sum\_tree\_1.jpg)

```
Input: root = [5,3,6,2,4,null,7], k = 9
Output: true
```

#### Solutions

{% tabs %}
{% tab title="DFS(Hashset) - O(n)" %}
{% hint style="success" %}
Time: O(n), Space: O(n)
{% endhint %}

{% hint style="info" %}
**Hint:** Keep a hashset of the nodes that have been seen and traverse the whole tree, if the difference between the `k-root.val` exists in the hashset, then you have found the Two Sum.
{% endhint %}

```python
def find_target(root: Optional[TreeNode], k: int) -> bool:
    seen = set()
    return dfs(root, k, seen)

def dfs(root, k, seen):
    if not root:
        return False
    if k-root.val in seen:
        return True
    seen.add(root.val)
    
    return dfs(root.left, k, seen) or dfs(root.right, k, seen)
```
{% endtab %}

{% tab title="BST(Hashset) - O(n)" %}
{% hint style="success" %}
Time: O(n), Space: O(n)
{% endhint %}

{% hint style="info" %}
**Hint:** BST normally uses a queue and in this approach, it just goes level by level using queue and the same idea with DFS, just check the difference of `k-node.val` and see if it exists in hashset where we keep track of the value of nodes that we've traversed.
{% endhint %}

```python
def find_target(root: Optional[TreeNode], k):
    if not root: 
        return False
    
    queue, seen = [root], set()
    while queue:
        node = queue.pop(0)
        if k - node.val in seen: 
            return True
        seen.add(node.val)
        
        if node.left: 
            queue.append(node.left)
        if node.right: 
            queue.append(node.right)
    
    return False
```
{% endtab %}
{% endtabs %}
