# Squares of Sorted Array

#### Links:

Squares of Sorted Array -[ ](https://leetcode.com/problems/maximum-subarray/)[https://leetcode.com/problems/squares-of-a-sorted-array/](https://leetcode.com/problems/squares-of-a-sorted-array/)

#### Problem:

Given an integer array `nums` sorted in **non-decreasing** order, return _an array of **the squares of each number** sorted in non-decreasing order_.

**Example 1:**

```
Input: nums = [-4,-1,0,3,10]
Output: [0,1,9,16,100]
Explanation: After squaring, the array becomes [16,1,0,9,100].
After sorting, it becomes [0,1,9,16,100].
```

#### Solutions

{% tabs %}
{% tab title="Sorting - O(n log n)" %}
{% hint style="success" %}
Time: O(n log n), Space: O(n)
{% endhint %}

{% hint style="info" %}
**Hint:** Square value then sort them.
{% endhint %}

```python
def sortedSquares(self, A):
    return sorted(x*x for x in A)
```
{% endtab %}

{% tab title="Three Pointer - O(n)" %}
{% hint style="success" %}
Time: O(n), Space: O(n)
{% endhint %}

{% hint style="info" %}
**Hint:** Have 3 pointer that'll traverse in reversal, where we place the square value between `left` and `right` to the `i` pointer of the result. The key is making the negative value absolute using `abs` so that when we compare a `-4` with `3`, the `-4` become `4` and it's greater than `3`.&#x20;

If `right` is greater than `left` then use it for squaring, else using `left`.&#x20;
{% endhint %}

```python
def sortedSquares(nums: List[int]) -> List[int]:
    result = [0]*len(nums)
    left = 0
    right = len(nums)-1
    
    for i in range(len(nums)-1,-1,-1):
        if abs(nums[right]) > abs(nums[left]):
            square = nums[right]
            right -= 1
        else:
            square = nums[left]
            left += 1
        result[i] = square*square
        
    return result
```
{% endtab %}
{% endtabs %}
