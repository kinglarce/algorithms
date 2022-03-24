# Binary Search

#### Links:

Binary Search -[ ](https://leetcode.com/problems/maximum-subarray/)[https://leetcode.com/problems/binary-search/](https://leetcode.com/problems/binary-search/)

#### Problem:

Given an array of integers `nums` which is sorted in ascending order, and an integer `target`, write a function to search `target` in `nums`. If `target` exists, then return its index. Otherwise, return `-1`.

You must write an algorithm with `O(log n)` runtime complexity.

**Example 1:**

```
Input: nums = [-1,0,3,5,9,12], target = 9
Output: 4
Explanation: 9 exists in nums and its index is 4
```

#### Solutions

{% tabs %}
{% tab title="Binary Search - O(log(n))" %}
{% hint style="success" %}
Time: O(log(n)), Space: O(1)
{% endhint %}

{% hint style="info" %}
**Hint:** Find the mid/pivot, if mid index value matches to `target` then return mid index, if not, then check, if mid < target, move left index to `mid + 1` otherwise adjust right index to `mid - 1.`&#x20;
{% endhint %}

```python
def search(nums: List[int], target: int) -> int:
    left = 0
    right = len(nums)-1
    
    while left <= right:
        mid = (left+right)//2
        
        if nums[mid] == target:
            return mid
        
        if nums[mid] < target: 
            left = mid + 1
        else:
            right = mid - 1
            
    return -1
```
{% endtab %}
{% endtabs %}

