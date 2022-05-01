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
**Hint:**&#x20;
{% endhint %}

```python
def threeSum(nums: List[int]) -> List[List[int]]:
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
