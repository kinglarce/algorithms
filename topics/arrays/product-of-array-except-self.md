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
**Hint:** Make two passes, first is left to right and second is right to left to compute the product. First pass is to calculate the prefix product for each index and another iteration is to calculate suffix product.&#x20;

![](https://assets.leetcode.com/users/images/99b64bb7-85d3-454e-a800-0a76cd905ef5\_1637980713.7155366.png)
{% endhint %}

```python
def product_array_except_self(nums):
    result = [1] * (len(nums))
    
    prefix = 1
    for i in range(len(nums)):
        result[i] = prefix
        prefix = prefix * nums[i]
        
    suffix = 1
    for i in range(len(nums)-1, -1, -1):
        result[i] = result[i] * suffix
        suffix = suffix * nums[i]

    return result
```
{% endtab %}

{% tab title="Division - O(n)" %}

{% endtab %}
{% endtabs %}
