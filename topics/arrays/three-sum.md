# Three Sum

#### Links:

Three Sum - [https://leetcode.com/problems/3sum/](https://leetcode.com/problems/3sum/)

#### Problem:

Given an integer array nums, return all the triplets `[nums[i], nums[j], nums[k]]` such that `i != j`, `i != k`, and `j != k`, and `nums[i] + nums[j] + nums[k] == 0`.

Notice that the solution set must not contain duplicate triplets.

**Example 1:**

```
Input: nums = [-1,0,1,2,-1,-4]
Output: [[-1,-1,2],[-1,0,1]]
```

#### Solutions

{% tabs %}
{% tab title="Two Pointer - O(n^2)" %}
{% hint style="success" %}
Time: O(n^2), Space: O(n)
{% endhint %}

{% hint style="info" %}
**Hint:** Similar to Two-Pointer approach in two sum where we sort the `nums` array first and then check if it's equal the target which is `0` , if it's greater, decrement the `right` pointer, if it's lesser, increment the `left` pointer, otherwise, it's already `0` . \
In this case, we use a third pointer which is `i` to basically use every number and then the `left` is `i+1` and `right` is `n-1` and sum up the three to see if it's equal to `0`

Validation is check if `curr_val` value is equals to previous value `nums[i-1]` , then that means we've already process that and skip it to avoid duplication.&#x20;
{% endhint %}

```python
def three_sum(nums: List[int]) -> List[List[int]]:
    nums.sort()
    result = []
    
    for i in range(len(nums)):
        curr_val = nums[i]
        if i > 0 and curr_val == nums[i-1]:
            continue
        left, right = i+1, len(nums)-1
        
        while left < right:
            total = curr_val + nums[left] + nums[right]
            if total == 0:
                result.append([curr_val, nums[left], nums[right]])
                
                left += 1
                while left < right and nums[left] == nums[left-1]:
                    left += 1
            elif total < 0:
                left += 1
            else:
                right -= 1
                
    return result
```
{% endtab %}
{% endtabs %}
