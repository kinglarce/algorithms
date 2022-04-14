# Search Insert Position

#### Links:

Search Insert Position -[ ](https://leetcode.com/problems/maximum-subarray/)[https://leetcode.com/problems/search-insert-position/](https://leetcode.com/problems/search-insert-position/)

#### Problem:

Given a sorted array of distinct integers and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.

You must write an algorithm with `O(log n)` runtime complexity.

**Example 1:**

```
Input: nums = [1,3,5,6], target = 5
Output: 2
```

#### Solutions

{% tabs %}
{% tab title="Binary Search - O(log(n))" %}
{% hint style="success" %}
Time: O(log(n)), Space: O(1)
{% endhint %}

{% hint style="info" %}
**Hint:** This is a typical Binary Search but if `target` value is not found, then return the potential place to insert it which is normally `left` index because at that point, `right` index and `left` index already overlapped.&#x20;
{% endhint %}

```python
def search_insert(nums: List[int], target: int) -> int:
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
            
    return left 
```
{% endtab %}
{% endtabs %}
