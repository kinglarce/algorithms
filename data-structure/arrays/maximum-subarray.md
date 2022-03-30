# Maximum Subarray

#### Links:

Maximum Subarray -[ ](https://leetcode.com/problems/maximum-subarray/)[https://leetcode.com/problems/maximum-subarray/](https://leetcode.com/problems/maximum-subarray/)

#### Problem:

Given an integer array `nums`, find the contiguous subarray (containing at least one number) which has the largest sum and return _its sum_.

A **subarray** is a **contiguous** part of an array.

**Example 1:**

```
Input: nums = [-2,1,-3,4,-1,2,1,-5,4]
Output: 6
Explanation: [4,-1,2,1] has the largest sum = 6.
```

#### Solutions

{% tabs %}
{% tab title="DP(Kadane Algo) - O(n)" %}
{% hint style="success" %}
Time: O(n), Space: O(1)
{% endhint %}

{% hint style="info" %}
**Hint:** Consider DP for getting maximum or minimum possibilities, and this uses Kadane's algorithms where is the current record number is worth keeping.
{% endhint %}

{% hint style="info" %}
**Hint 2:** Get max current sum plus current num or current num then adjust max sum if current sum is greater than max sum.
{% endhint %}

```python
def maxSubArray(nums: List[int]) -> int:
    curr_sum = nums[0]
    max_sum = nums[0]
    
    for i in range(1, len(nums)):
        curr_sum = max(nums[i], curr_sum + nums[i])
        max_sum = max(curr_sum, max_sum)
        
    return max_sum
```
{% endtab %}

{% tab title="Two Pointer - O(n^2)" %}
{% hint style="success" %}
Time: O(n^2), Space: O(1)
{% endhint %}

{% hint style="info" %}
**Hint:** Run a two pointer from left to right and get the max sum from left pointer to right pointer.
{% endhint %}

```python
def maxSubArray(nums: List[int]) -> int:
    max_subarray = float('-inf')
    for left in range(len(nums)):
        current_subarray = 0
        for right in range(left, len(nums)):
            current_subarray += nums[right]
            max_subarray = max(max_subarray, current_subarray)
    
    return max_subarray
```
{% endtab %}
{% endtabs %}
