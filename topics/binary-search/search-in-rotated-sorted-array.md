# Search in Rotated Sorted Array

#### Links:

Search in Rotated Sorted Array -[ ](https://leetcode.com/problems/maximum-subarray/)[https://leetcode.com/problems/search-in-rotated-sorted-array/](https://leetcode.com/problems/search-in-rotated-sorted-array/)

#### Problem:

Given the array `nums` **after** the possible rotation and an integer `target`, return _the index of_ `target` _if it is in_ `nums`_, or_ `-1` _if it is not in_ `nums`.

You must write an algorithm with `O(log n)` runtime complexity.

**Example 1:**

```
Input: nums = [4,5,6,7,0,1,2], target = 0
Output: 4
```

**Example 2:**

```
Input: nums = [2,4,5,6,7,0,1], target = 5
Output: 2
```

#### Solutions

{% tabs %}
{% tab title="Binary Search - O(log(n))" %}
{% hint style="success" %}
Time: O(log(n)), Space: O(1)
{% endhint %}

{% hint style="info" %}
**Hint:** Instead of finding the rotated index like the "Find Minimum in Rotated Sorted Array", we just need to find which non-rotated subarray to look for and do a binary search.

If `nums[mid]` equals `target` then all good, but there are 4 key points

If `nums[left]` is less than or equal to `nums[mid`] then the left to mid subarray is non-rotated and we shall start looking there.

If `target` value is in between of the `nums[left]` and `nums[mid]` which is the left half non-rotated subarray, then we adjust the `right` pointer, otherwise, we adjust the `left` pointer since we're at the wrong half and our `target` value is on the right half of it.

If `nums[left]`, is greater than `nums[mid]` then the mid to right subarray is non-rotated and we shall start looking there.

If `target` value is in between of the `nums[mid]` and `nums[right]` which is the right half non-rotated subarray, then we adjust the `left` pointer, otherwise, we adjust the `right` pointer since we're at the wrong half and our `target` value is on the left half of it.
{% endhint %}

```python
def search(nums: List[int], target: int) -> int:
    left, right = 0, len(nums)-1
    
    while left <= right:
        mid = (left+right)//2

        if nums[mid] == target:
            return mid
        
        if nums[left] <= nums[mid]:
            if nums[left] <= target and target < nums[mid]:
                right = mid - 1
            else:
                left = mid + 1
        else:
            if nums[mid] < target and target <= nums[right]:
                left = mid + 1
            else:
                right = mid - 1
                
    return -1
```
{% endtab %}
{% endtabs %}
