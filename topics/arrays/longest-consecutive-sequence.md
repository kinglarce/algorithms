# Longest Consecutive Sequence

#### Links:

Longest Consecutive Sequence - [https://leetcode.com/problems/longest-consecutive-sequence/](https://leetcode.com/problems/longest-consecutive-sequence/)

#### Problem:

Given an unsorted array of integers `nums`, return _the length of the longest consecutive elements sequence._

You must write an algorithm that runs in `O(n)` time.

**Example 1:**

```
Input: nums = [100,4,200,1,3,2]
Output: 4
Explanation: The longest consecutive elements sequence is [1, 2, 3, 4]. Therefore its length is 4.
```

**Example 2:**

```
Input: nums = [0,3,7,2,5,8,4,6,0,1]
Output: 9
```

#### Solutions

{% tabs %}
{% tab title="HashSets - O(n)" %}
{% hint style="success" %}
Time: O(n), Space: O(n) - The for loop and while loop is O(n + n)
{% endhint %}

{% hint style="info" %}
**Hint:**  Create a `set` of `nums` to have a reference if the number exists. Go through the numbers and check if the previous number exists in the `uniq_nums` , if it doesn't, then the that's the start of the sequence, and now check if the next number which is `next_num` is in the `uniq_nums` , if not, then we don't have the sequence and move forward to another number.\
eg.\
\[1,2,3,4] -- \[100] -- \[200]
{% endhint %}

```python
def longest_consecutive(nums: List[int]) -> int:
    uniq_nums = set(nums)
    longest = 0
    
    for num in nums:
        if num-1 not in uniq_nums:
            next_num = num+1
            
            while next_num in uniq_nums:
                next_num += 1
                
            longest = max(longest, next_num - num)
            
    return longest
```
{% endtab %}

{% tab title="Sorted - O(n log n)" %}
{% hint style="success" %}
Time: O(n log n), Space: O(n)
{% endhint %}

{% hint style="info" %}
**Hint:** &#x20;
{% endhint %}

```python
def longest_consecutive(nums: List[int]) -> int:
    if not nums:
        return 0
    
    nums = sorted(nums)
    longest = 1
    sub_longest = 1
    
    for i in range(len(nums)-1):
        
        if nums[i] + 1 < nums[i+1]:
            sub_longest = 1
        elif nums[i] + 1 == nums[i+1]:
            sub_longest += 1
        
        longest = max(longest, sub_longest)
        
    return longest
```
{% endtab %}
{% endtabs %}
