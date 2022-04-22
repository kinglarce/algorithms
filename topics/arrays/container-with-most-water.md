# Container With Most Water

#### Links:

Container with Most Water - [https://leetcode.com/problems/container-with-most-water/](https://leetcode.com/problems/container-with-most-water/)

#### Problem:

You are given an integer array `height` of length `n`. There are `n` vertical lines drawn such that the two endpoints of the `ith` line are `(i, 0)` and `(i, height[i])`.

Find two lines that together with the x-axis form a container, such that the container contains the most water.

Return _the maximum amount of water a container can store_.

**Notice** that you may not slant the container.

**Example 1:**

![](https://s3-lc-upload.s3.amazonaws.com/uploads/2018/07/17/question\_11.jpg)

```
Input: height = [1,8,6,2,5,4,8,3,7]
Output: 49
Explanation: The above vertical lines are represented by array [1,8,6,2,5,4,8,3,7]. In this case, the max area of water (blue section) the container can contain is 49.
```

#### Solutions

{% tabs %}
{% tab title="Two Pointer - O(n)" %}
{% hint style="success" %}
Time: O(n), Space: O(1)
{% endhint %}

{% hint style="info" %}
**Hint:**&#x20;
{% endhint %}

```python
def max_area(height: List[int]) -> int:
    max_area = 0
    left, right = 0, len(height)-1
    
    while left < right:
        delta = right - left
        area = delta * min(height[left], height[right])
        max_area = max(max_area, area)
        
        if height[left] <= height[right]:
            left += 1
        else:
            right -= 1
            
    return max_area
```
{% endtab %}
{% endtabs %}
