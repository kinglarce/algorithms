# Flood Fill

#### Links:

Flood Fill - [https://leetcode.com/problems/flood-fill/](https://leetcode.com/problems/flood-fill/)

#### Problem:

An image is represented by an `m x n` integer grid `image` where `image[i][j]` represents the pixel value of the image.

You are also given three integers `sr`, `sc`, and `newColor`. You should perform a **flood fill** on the image starting from the pixel `image[sr][sc]`.

To perform a **flood fill**, consider the starting pixel, plus any pixels connected **4-directionally** to the starting pixel of the same color as the starting pixel, plus any pixels connected **4-directionally** to those pixels (also with the same color), and so on. Replace the color of all of the aforementioned pixels with `newColor`.

Return _the modified image after performing the flood fill_.

**Example 1:**

![](https://assets.leetcode.com/uploads/2021/06/01/flood1-grid.jpg)

```
Input: image = [[1,1,1],[1,1,0],[1,0,1]], sr = 1, sc = 1, newColor = 2
Output: [[2,2,2],[2,2,0],[2,0,1]]
Explanation: From the center of the image with position (sr, sc) = (1, 1) (i.e., the red pixel), all pixels connected by a path of the same color as the starting pixel (i.e., the blue pixels) are colored with the new color.
Note the bottom corner is not colored 2, because it is not 4-directionally connected to the starting pixel.
```

#### Solutions

{% tabs %}
{% tab title="DFS - O(n)" %}
{% hint style="success" %}
Time: O(n), Space: O(n)
{% endhint %}

{% hint style="info" %}
**Hint:** Using DFS, check the 4 neighboring pixels are the same value with `image[sr][sc]` which is the starting point and replace it with `new_color`, if not, then we skip it. To prevent going back in the previous direction, keep track of what has been visited using `seen`.
{% endhint %}

```python
def flood_fill(image: List[List[int]], sr: int, sc: int, new_color: int) -> List[List[int]]:
    color = image[sr][sc]
    seen = set()
    dfs(image, sr, sc, new_color, color, seen)
    return image
    
def dfs(image, row, col, new_color, color, seen):
    if row < 0 or row >= len(image) or col < 0 or col >= len(image[0]) or image[row][col] != color or (row, col) in seen:
        return
    seen.add((row, col))
    image[row][col] = new_color
    dfs(image, row-1, col, new_color, color, seen)
    dfs(image, row+1, col, new_color, color, seen)
    dfs(image, row, col-1, new_color, color, seen)
    dfs(image, row, col+1, new_color, color, seen)
```
{% endtab %}
{% endtabs %}
