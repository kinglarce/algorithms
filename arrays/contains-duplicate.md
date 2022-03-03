# Contains Duplicate

#### Links:

Contains Duplicate -[ ](https://leetcode.com/problems/contains-duplicate/)[https://leetcode.com/problems/contains-duplicate/](https://leetcode.com/problems/contains-duplicate/)

#### Problem:

Given an integer array `nums`, return `true` if any value appears **at least twice** in the array, and return `false` if every element is distinct.

**Example 1:**

```
Input: nums = [1,2,3,1]
Output: true
```

#### Solutions

{% tabs %}
{% tab title="Sorting - O(nlogn)" %}
{% hint style="success" %}
Time: O(nlogn), Space: O(1)
{% endhint %}

{% hint style="info" %}
**Hint:** Sort it and check the adjacent value.
{% endhint %}

```python
def contains_duplicate(nums):
    nums.sort()
    for i in range(len(nums)-1):
        if nums[i] == nums[i+1]:
            return True
    return False
```
{% endtab %}

{% tab title="Comparing Unique - O(n)" %}
{% hint style="success" %}
Time: O(n), Space: O(1)
{% endhint %}

{% hint style="info" %}
**Hint:** Change to Set to get unique values and comapre
{% endhint %}

```python
def contains_duplicate(nums):
    nums_set = list(set(nums))
    return not (len(nums_set) == len(nums))
```
{% endtab %}

{% tab title="Check If It Exist - O(n)" %}
{% hint style="success" %}
Time: O(n), Space: O(1)
{% endhint %}

{% hint style="info" %}
**Hint:** Check if it's already recorded in Set/Hashmap
{% endhint %}

```python
def contains_duplicate(nums):
    uniq_nums = set()
    for num in nums:
        if num in uniq_nums:
            return True
        uniq_nums.add(num)
    return False
```
{% endtab %}
{% endtabs %}

