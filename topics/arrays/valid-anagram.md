# Valid Anagram

#### Links:

Valid Anagram -[ ](https://leetcode.com/problems/maximum-subarray/)[https://leetcode.com/problems/valid-anagram/](https://leetcode.com/problems/valid-anagram/)

#### Problem:

Given two strings `s` and `t`, return `true` _if_ `t` _is an anagram of_ `s`_, and_ `false` _otherwise_.

An **Anagram** is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

**Example 1:**

```
Input: s = "anagram", t = "nagaram"
Output: true
```

#### Solutions

{% tabs %}
{% tab title="Hashmap - O(n)" %}
{% hint style="success" %}
Time: O(n), Space: O(1) - English alphabet is fix 26 letters
{% endhint %}

{% hint style="info" %}
**Hint:** Get the frequency of characters of `s` .

Iterate the 2nd string `t` , check if character exists on hashmap, if it is, then reduce it, check again if the frequency of that character is greater than `0` . Finally, sum up all the frequency value if `0` then it's valid, otherwise, it's not.
{% endhint %}

```python
 def is_anagram(s: str, t: str) -> bool:
    if len(s) != len(t):
        return False
    
    freq = {}
    for c in s:
        freq[c] = 1 + freq.get(c, 0)
      
    for c in t:
        if c not in freq:
            return False
        freq[c] -= 1
        if freq[c] < 0:
            return False
    
    
    return True if sum(freq.values()) == 0 else False
```
{% endtab %}

{% tab title="Sorting - O(n log n)" %}
{% hint style="success" %}
Time: O(n log n), Space: O(1) - O(n log n) is because of the sorting functionality.
{% endhint %}

{% hint style="info" %}
**Hint:** Sort and compare.
{% endhint %}

```python
 def is_anagram(self, s: str, t: str) -> bool:
    if len(s) != len(t):
        return False

    return sorted(s) == sorted(t)
```
{% endtab %}
{% endtabs %}
