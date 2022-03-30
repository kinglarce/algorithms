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
{% tab title="Sorting - O(n log n)" %}
{% hint style="success" %}
Time: O(nlogn), Space: O(1)
{% endhint %}

{% hint style="info" %}
**Hint:** Sort and compare current value with next value if its the same.
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

{% tab title="Set - O(n)" %}
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

{% tab title="Set/Hashmap - O(n)" %}
{% hint style="success" %}
Time: O(n), Space: O(1)
{% endhint %}

{% hint style="info" %}
**Hint:** Record each num in unique set if it doesn't exist, else, return True.
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
