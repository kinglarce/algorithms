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
Time: O(n), Space: O(26) - Time is O(26\*n) because of getting the max frequency
{% endhint %}

{% hint style="info" %}
**Hint:**  Run `left` and `right` pointer where `right` run through the array and collect the character frequency and `left` adjust when possible replacment is over `k`.

There are 3 key points

Get the character frequency which will be used for getting the max later on.

Subtract the delta which is `right - left + 1` with max character frequency `max(count.values())` if it's over `k`, if it's over `k` then adjust the `left` pointer and decrement the `left` pointer character. This behavior will minimize the window which minimizes the delta value as well for the longest possible replacement.

Finally, the longest possible replacement for characters is the delta `right - left + 1` and just get the max between the `result`.
{% endhint %}

```python
def character_replacement(s: str, k: int) -> int:
    count = {}
    left = 0
    result = 0
    
    for right in range(len(s)):
        index = s[right]
        count[index] = 1 + count.get(index, 0)
        
        while (right - left + 1) - max(count.values()) > k:
            count[s[left]] -= 1
            left += 1
        
        result = max(result, right - left + 1)
        
    return result
```
{% endtab %}
{% endtabs %}
