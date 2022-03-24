# Merge Sorted Array



#### Links:

Merge Sorted Array -[ ](https://leetcode.com/problems/maximum-subarray/)[https://leetcode.com/problems/merge-sorted-array/](https://leetcode.com/problems/merge-sorted-array/)

#### Problem:

You are given two integer arrays `nums1` and `nums2`, sorted in **non-decreasing order**, and two integers `m` and `n`, representing the number of elements in `nums1` and `nums2` respectively.

**Merge** `nums1` and `nums2` into a single array sorted in **non-decreasing order**.

The final sorted array should not be returned by the function, but instead be _stored inside the array_ `nums1`. To accommodate this, `nums1` has a length of `m + n`, where the first `m` elements denote the elements that should be merged, and the last `n` elements are set to `0` and should be ignored. `nums2` has a length of `n`.

**Example 1:**

```
Input: nums1 = [1,2,3,0,0,0], m = 3, nums2 = [2,5,6], n = 3
Output: [1,2,2,3,5,6]
Explanation: The arrays we are merging are [1,2,3] and [2,5,6].
The result of the merge is [1,2,2,3,5,6] with the underlined elements coming from nums1.
```

#### Solutions

{% tabs %}
{% tab title="Three Pointer(w/ Space) - O(m+n)" %}
{% hint style="success" %}
Time: O(m+n), Space: O(m)
{% endhint %}

{% hint style="info" %}
**Hint:** Have 3 pointer that'll traverse to `nums1_copy`, `nums1` and `nums2`, Since we're gonna be modifying in-place, that's why we have a `nums1_copy` for retrieving the value and `nums` which is the original array and a place to replace the value.

Compare `nums1_copy` value if it's less than `nums2` value, if it is, then just replace `nums1[p3]` value with whatever is less than then also move the `p1` and `p2` pointer according.
{% endhint %}

{% hint style="info" %}
Hint 2: Keep in mind the boundaries, if `p1` is over `m` boundaries, the same goes for `p2`.

`if p2 >= n` to check if `nums2` could potentially be empty, then just add `nums1_copy` values, or `p1 < m` to check if `p1` is within `m` boundaries.&#x20;
{% endhint %}

```python
def merge(nums1: List[int], m: int, nums2: List[int], n: int) -> None:
    """
    Do not return anything, modify nums1 in-place instead.
    """
    nums1_copy = nums1[:m]
    
    p1 = 0
    p2 = 0
    for p3 in range(n+m):
        
        if p2 >= n or (p1 < m and nums1_copy[p1] <= nums2[p2]):
            nums1[p3] = nums1_copy[p1]
            p1 += 1
        else:
            nums1[p3] = nums2[p2]
            p2 += 1
```
{% endtab %}

{% tab title="Three Pointer - O(m+n)" %}
{% hint style="success" %}
Time: O(m+n), Space: O(1)
{% endhint %}

{% hint style="info" %}
**Hint:** Have 3 pointer that'll traverse in reversal, where we place the greater value between `nums1` and `nums2` and place it to `p3` location until `p3` reach to index 0.

Keep in mind the boundaries, if `p2` is already reach 0, then we don't need to modify `nums1` anymore and should be understood that it's already been sorted.
{% endhint %}

```python
def merge(nums1: List[int], m: int, nums2: List[int], n: int) -> None:
    """
    Do not return anything, modify nums1 in-place instead.
    """
    p1 = m - 1
    p2 = n - 1

    # And move p backwards through the array, each time writing
    # the smallest value pointed at by p1 or p2.
    for p3 in range(n + m - 1, -1, -1):
        if p2 < 0:
            break
        if p1 >= 0 and nums1[p1] > nums2[p2]:
            nums1[p3] = nums1[p1]
            p1 -= 1
        else:
            nums1[p3] = nums2[p2]
            p2 -= 1
```
{% endtab %}
{% endtabs %}
