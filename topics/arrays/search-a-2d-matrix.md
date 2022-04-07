# Search a 2D Matrix

#### Links:

Search a 2D Matrix -[ ](https://leetcode.com/problems/maximum-subarray/)[https://leetcode.com/problems/search-a-2d-matrix/](https://leetcode.com/problems/search-a-2d-matrix/)

#### Problem:

Write an efficient algorithm that searches for a value `target` in an `m x n` integer matrix `matrix`. This matrix has the following properties:

* Integers in each row are sorted from left to right.
* The first integer of each row is greater than the last integer of the previous row.&#x20;

**Example 1:**

![](https://assets.leetcode.com/uploads/2020/10/05/mat.jpg)

```
Input: matrix = [[1,3,5,7],[10,11,16,20],[23,30,34,60]], target = 3
Output: true
```

#### Solutions

{% tabs %}
{% tab title="Binary Search - O(log n)" %}
{% hint style="success" %}
Time: O(log n), Space: O(1)
{% endhint %}

{% hint style="info" %}
**Hint:** Do binary search both top-bottom and left-right.

Top-Bottom, get the middle and check end-to-end if  `target` is less than`matrix[mid][0]` or greater than `matrix[mid][-1]` then adjust the middle, otherwise, then you already find the middle for Left-Right binary search later on.

Left-Right, do binary search with `matrix[(top+bot)//2]`.
{% endhint %}

```python
def search_matrix(matrix: List[List[int]], target: int) -> bool:
    m = len(matrix)
    n = len(matrix[0])
    
    top, bot = 0, m-1
    row = None
    
    while top <= bot:
        mid = (top+bot)//2
        
        if target < matrix[mid][0]:
            bot = mid-1
        elif target > matrix[mid][-1]:
            top = mid+1
        else:
            break
            
    left, right = 0, n-1
    row = matrix[(top+bot)//2]
    
    while row and left <= right:
        mid = (left+right)//2
        
        if target < row[mid]:
            right = mid-1
        elif target > row[mid]:
            left = mid+1
        else:
            return True
        
    return False
```
{% endtab %}

{% tab title="Space Reduction - O(m+n)" %}
{% hint style="success" %}
Time: O(m+n), Space: O(1)
{% endhint %}

{% hint style="info" %}
**Hint:** Start from bottom-left, if the current matrix value `matrix[row][col]` is greater than `target`, then go up, if it's smaller than the `target` then go right until it equals to the `target` value.

This only works if matrix is sorted.
{% endhint %}

```python
def search_matrix(matrix: List[List[int]], target: int) -> bool:
    if not len(matrix):
        return False
    
    m = len(matrix)
    n = len(matrix[0])
    
    row = m-1
    col = 0
    
    while row >= 0 and col < n:
        
        if matrix[row][col] > target:
            row -= 1
        elif matrix[row][col] < target:
            col += 1
        else:
            return True
        
    return False
```
{% endtab %}
{% endtabs %}
