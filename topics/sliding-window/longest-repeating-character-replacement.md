# Longest Repeating Character Replacement

#### Links:

Longest Repeating Character Replacement - [https://leetcode.com/problems/longest-repeating-character-replacement/](https://leetcode.com/problems/longest-repeating-character-replacement/)

#### Problem:

You are given a string `s` and an integer `k`. You can choose any character of the string and change it to any other uppercase English character. You can perform this operation at most `k` times.

Return _the length of the longest substring containing the same letter you can get after performing the above operations_.

**Example 1:**

```
Input: s = "ABAB", k = 2
Output: 4
Explanation: Replace the two 'A's with two 'B's or vice versa.
```

**Example 2:**

```
Input: s = "AABABBA", k = 1
Output: 4
Explanation: Replace the one 'A' in the middle with 'B' and form "AABBBBA".
The substring "BBBB" has the longest repeating letters, which is 4.
```

#### Solutions

{% tabs %}
{% tab title="Sliding Window - O(n)" %}
{% hint style="success" %}
Time: O(n), Space: O(n)
{% endhint %}

{% hint style="info" %}
**Hint:** &#x20;
{% endhint %}

```python
def characterReplacement(self, s: str, k: int) -> int:
    count = {}
    left = 0
    result = 0
    
    for right in range(len(s)):
        index = s[right]
        count[index] = 1 + count.get(index, 0)
        
        while right - left + 1 - max(count.values()) > k:
            count[s[left]] -= 1
            left += 1
        
        result = max(result, right - left + 1)
        
    return result
```
{% endtab %}
{% endtabs %}
