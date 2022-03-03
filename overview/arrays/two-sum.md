# Two Sum

#### Links:

Two Sum - [https://leetcode.com/problems/two-sum/](https://leetcode.com/problems/two-sum/)

Two Sum II - [https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/)

#### Problem:

Given an array of integers `nums` and an integer `target`, return _indices of the two numbers such that they add up to `target`_.

You may assume that each input would have _**exactly**_** one solution**, and you may not use the _same_ element twice.

You can return the answer in any order.

**Example 1:**

```
Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].
```

#### Solutions

{% tabs %}
{% tab title="Two Loop - O(n^2)" %}
{% hint style="success" %}
Time: O(n^2), Space: O(1)
{% endhint %}

{% hint style="info" %}
**Hint:** Use two-loop for and sum the two number if it matches the target
{% endhint %}

```python
def two_sum(nums, target):
	for i in range(len(nums)):
		for j in range(i + 1, len(nums)):
			if (nums[i]+nums[j]) == target:
				return [i, j]
```
{% endtab %}

{% tab title="Hashmap - O(n)" %}
{% hint style="success" %}
Time: O(n), Space: O(n)
{% endhint %}

{% hint style="info" %}
**Hint:** Use hashmap/dictionary by recording the subracted value of `target` and `nums[i]` and use it to check if one of the value in the `nums` array already exist in the dictionary.
{% endhint %}

```python
def two_sum(nums, target):
    uniq = {}
    for i in range(len(nums)): 
        num_diff = abs(target-nums[i])
        if not num_diff in uniq:
            uniq[nums[i]] = True
        else:
            return [nums[i], num_diff]
    return False
```
{% endtab %}

{% tab title="Pointer - O(n)/O(nlogn)" %}
{% hint style="success" %}
Time: O(n), Space: O(1)
{% endhint %}

{% hint style="info" %}
**Hint 1:** Assuming the nums is already `sorted` then we can use `left` and `right` pointer, if it's not sorted, then we need to sort the `nums` array. Sortingting the `nums` array by using `nums.sort()` could change the time complexity to `O(n log n).`
{% endhint %}

{% hint style="info" %}
**Hint 2**: Use `left` pointer starting from leftmost and `right` pointer starting from the end of the array to run each of the values on the way to the middle.
{% endhint %}

```python
def two_sum(nums, target):
    left, right = 0, len(nums)-1
    while left < right:
        total = nums[left]+nums[right]
        if total == target:
            return [left+1, right+1]
        elif total < target:
            left += 1
        else:
            right -= 1
    return -1
```
{% endtab %}
{% endtabs %}

