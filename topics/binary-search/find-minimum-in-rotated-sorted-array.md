# Find Minimum in Rotated Sorted Array

#### Links:

Find Minimum in Rotated Sorted Array -[ ](https://leetcode.com/problems/maximum-subarray/)[https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/)

#### Problem:

Suppose an array of length `n` sorted in ascending order is **rotated** between `1` and `n` times. For example, the array `nums = [0,1,2,4,5,6,7]` might become:

* `[4,5,6,7,0,1,2]` if it was rotated `4` times.
* `[0,1,2,4,5,6,7]` if it was rotated `7` times.

Notice that **rotating** an array `[a[0], a[1], a[2], ..., a[n-1]]` 1 time results in the array `[a[n-1], a[0], a[1], a[2], ..., a[n-2]]`.

Given the sorted rotated array `nums` of **unique** elements, return _the minimum element of this array_.

You must write an algorithm that runs in `O(log n) time.`

**Example 1:**

```
Input: nums = [3,4,5,1,2]
Output: 1
Explanation: The original array was [1,2,3,4,5] rotated 3 times.
```

**Example 2:**

```
Input: nums = [4,5,6,7,0,1,2]
Output: 0
Explanation: The original array was [0,1,2,4,5,6,7] and it was rotated 4 times.
```

#### Solutions

{% tabs %}
{% tab title="Binary Search - O(log(n))" %}
{% hint style="success" %}
Time: O(log(n)), Space: O(1)
{% endhint %}

{% hint style="info" %}
**Hint:** There are 3 key points

Find rotate index which is the smallest by check if the previous number which is `nums[mid-1]` is greater than the current number `nums[mid]`

Adjusting `left` pointer if `nums[mid]` is greater than the `nums[right]` and vice-versa

Finally, return the `nums[left]` because `left` and `right` pointer already overlapped and that could be the minimum number.
{% endhint %}

```python
def find_min(nums: List[int]) -> int:
    left, right = 0, len(nums)-1
    
    while left < right:
        mid = (left+right)//2
        
        if mid > 0 and nums[mid-1] > nums[mid]:
            return nums[mid]
        
        if nums[mid] > nums[right]:
            left = mid + 1
        else:
            right = mid -1 
            
    return nums[left]
```
{% endtab %}
{% endtabs %}
