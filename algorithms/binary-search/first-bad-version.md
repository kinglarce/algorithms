# First Bad Version

#### Links:

First Bad Version -[ ](https://leetcode.com/problems/maximum-subarray/)[https://leetcode.com/problems/first-bad-version/](https://leetcode.com/problems/first-bad-version/)

#### Problem:

You are a product manager and currently leading a team to develop a new product. Unfortunately, the latest version of your product fails the quality check. Since each version is developed based on the previous version, all the versions after a bad version are also bad.

Suppose you have `n` versions `[1, 2, ..., n]` and you want to find out the first bad one, which causes all the following ones to be bad.

You are given an API `bool isBadVersion(version)` which returns whether `version` is bad. Implement a function to find the first bad version. You should minimize the number of calls to the API.

**Example 1:**

```
Input: n = 5, bad = 4
Output: 4
Explanation:
call isBadVersion(3) -> false
call isBadVersion(5) -> true
call isBadVersion(4) -> true
Then 4 is the first bad version.
```

#### Solutions

{% tabs %}
{% tab title="Binary Search - O(log(n))" %}
{% hint style="success" %}
Time: O(log(n)), Space: O(1)
{% endhint %}

{% hint style="info" %}
**Hint:** Find the mid/pivot, check if `mid` is **bad** and its previous index is **not bad**, then that could be the answer, but also keep in mind the boundaries if `mid` index is greater than 0 or else it'll be out of bounds when checking the previous index.

&#x20;If `mid` is **not bad** then adjust the `left` index, otherwise, adjust the `right` index.
{% endhint %}

```python
# The isBadVersion API is already defined for you.
# def isBadVersion(version: int) -> bool:

def firstBadVersion(n: int) -> int:
    left = 0 
    right = n
    
    while left <= right:
        mid = (left+right)//2
        
        if mid > 0 and (isBadVersion(mid-1) is False and isBadVersion(mid) is True):
            return mid
        
        if isBadVersion(mid):
            right = mid - 1 
        else:
            left = mid + 1
            
    return -1 
```
{% endtab %}
{% endtabs %}
