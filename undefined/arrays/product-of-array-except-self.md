# Product of Array Except Self

#### Links:

Product of Array Except Self-[ ](https://leetcode.com/problems/contains-duplicate/)[https://leetcode.com/problems/product-of-array-except-self/](https://leetcode.com/problems/product-of-array-except-self/)

#### Problem:

Given an integer array `nums`, return _an array_ `answer` _such that_ `answer[i]` _is equal to the product of all the elements of_ `nums` _except_ `nums[i]`.

The product of any prefix or suffix of `nums` is **guaranteed** to fit in a **32-bit** integer.

You must write an algorithm that runs in `O(n)` time and without using the division operation.

**Example 1:**

```
Input: nums = [1,2,3,4]
Output: [24,12,8,6]
```

#### Solutions

{% tabs %}
{% tab title="Two Passes - O(n)" %}
{% hint style="success" %}
Time: O(n), Space: O(1)
{% endhint %}

{% hint style="info" %}
**Hint:** Make two passes, first is left to right and second is right to left to compute the product.
{% endhint %}

```python
def product_array_except_self(nums):
    result = [1] * (len(nums))
    prefix = 1
    for i in range(len(nums)):
        result[i] = prefix
        prefix = prefix * nums[i]
    postfix = 1
    for i in range(len(nums)-1, -1, -1):
        result[i] = result[i] * postfix
        postfix = postfix * nums[i]

    return result
```
{% endtab %}
{% endtabs %}

