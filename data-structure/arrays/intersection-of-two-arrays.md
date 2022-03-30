# Intersection of Two Arrays

#### Links:

Intersection of Two Arrays-[ ](https://leetcode.com/problems/maximum-subarray/)[https://leetcode.com/problems/intersection-of-two-arrays-ii/](https://leetcode.com/problems/intersection-of-two-arrays-ii/)

#### Problem:

Given two integer arrays `nums1` and `nums2`, return _an array of their intersection_. Each element in the result must appear as many times as it shows in both arrays and you may return the result in **any order**.

**Example 1:**

```
Input: nums1 = [1,2,2,1], nums2 = [2,2]
Output: [2,2]
```

#### Solutions

{% tabs %}
{% tab title="Sorting - O(n log n)" %}
{% hint style="success" %}
Time: O(n log n), Space: O(n)
{% endhint %}

{% hint style="info" %}
**Hint:** "Intersection" just means the same value from both arrays.

Sort `nums1` and `nums2` so that you can presume that it's ascending order and easy to compare two arrays using two-pointers.

Compare `nums1[i]` and `nums2[j]` if `nums1[i]` is less than `nums2[j]` then move forward the `i` pointer, if it's greater then move forward the `j` pointer otherwise then that's the intersection. ``&#x20;
{% endhint %}

```python
def intersect(nums1: List[int], nums2: List[int]) -> List[int]:
    nums1.sort()
    nums2.sort()
    result = []
    
    i = j = 0
    
    while i < len(nums1) and j < len(nums2):
        if nums1[i] == nums2[j]:
            result.append(nums1[i])
            j += 1
            i += 1
        elif nums1[i] < nums2[j]:
            i += 1
        else:
            j += 1
            
    return result
```
{% endtab %}

{% tab title="Hashmap - O(n)" %}
{% hint style="success" %}
Time: O(n), Space: O(n)
{% endhint %}

{% hint style="info" %}
**Hint:** Get the frequency of numbers in `nums1` and put it in the hashmap.

Iterate over `nums2` if value is in the `frequency` hashmap and it's still greater than `0` then add it to the `result` and reduce it to invalidate the usage of that number from `nums1.`
{% endhint %}

```python
def intersect(nums1: List[int], nums2: List[int]) -> List[int]:
    frequency = {}
    result = []
    
    for num in nums1:
        frequency[num] = frequency.get(num, 0) + 1
        
    for num in nums2:
        if num in frequency and frequency[num] > 0:
            frequency[num] -= 1
            result.append(num)
            
    return result
```
{% endtab %}
{% endtabs %}
