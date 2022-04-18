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
def product_array_except_self(nums: List[int]) -> List[int]:
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
{% hint style="success" %}
Time: O(n), Space: O(1)
{% endhint %}

{% hint style="info" %}
**Hint:** Idea is to get the product by multiplying each number in `nums` and then afterward is just divide them, but the edge case is that what if one of the numbers is 0. So, we need to keep track of 0, if it's only one, then when we reach the 0 `num` , then we can just use the `product` which is the product of the numbers before and after the `num` 0. But, if there are two 0, then it's nearly impossible for us to have a product and just make every number in the result 0.
{% endhint %}

```python
def product_array_except_self(nums: List[int]) -> List[int]: 
    product = 1
    zero_count = 0

    for num in nums:
        if num != 0:
            product = product * num
        else:
            zero_count += 1

    if zero_count > 1:
        return [0]*len(nums)
    elif zero_count == 1:
        return [product if num == 0 else 0 for num in nums]
    else:
        return [product//num for num in nums]
```
{% endtab %}
{% endtabs %}
