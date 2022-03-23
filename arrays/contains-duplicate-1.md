# Contains Duplicate

#### Links:

Contains Duplicate - [https://leetcode.com/problems/contains-duplicate/](https://leetcode.com/problems/contains-duplicate/)

#### Problem:

Given an integer array `nums`, return `true` if any value appears **at least twice** in the array, and return `false` if every element is distinct.

**Example 1:**

```
Input: nums = [1,2,3,1]
Output: true
```

#### Solutions

{% tabs %}
{% tab title="Hashmap - O(n)" %}
{% hint style="success" %}
Time: O(n), Space: O(n)
{% endhint %}

{% hint style="info" %}
**Hint:** Record each num in unique set if it doesn't exist, else, return True
{% endhint %}

```python
def containsDuplicate(nums: List[int]) -> bool:
    uniq = set()

    for num in nums:
        if num in uniq:
            return True
        uniq.add(num)
        
    return False
```
{% endtab %}
{% endtabs %}

