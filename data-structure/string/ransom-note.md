# Ransom Note

#### Links:

Ransom Note -[ ](https://leetcode.com/problems/maximum-subarray/)[https://leetcode.com/problems/ransom-note](https://leetcode.com/problems/ransom-note)

#### Problem:

Given two strings `ransomNote` and `magazine`, return `true` _if_ `ransomNote` _can be constructed from_ `magazine` _and_ `false` _otherwise_.

Each letter in `magazine` can only be used once in `ransomNote`.

**Example 1:**

```
Input: ransomNote = "a", magazine = "b"
Output: false
```

**Example 2:**

```
Input: ransomNote = "aa", magazine = "ab"
Output: false
```

#### Solutions

{% tabs %}
{% tab title="Hashmap - O(n)" %}
{% hint style="success" %}
Time: O(n), Space: O(1) - English alphabet is fix 26 letters
{% endhint %}

{% hint style="info" %}
**Hint:** It's the same as Valid Anagram, get the frequency of characters, check if it exists and check if frequency is not less than `0` , then just return `True.`
{% endhint %}

```python
 def can_construct(ransomNote: str, magazine: str) -> bool:
    char_freq = {}
    
    for c in magazine:
        char_freq[c] = char_freq.get(c, 0) + 1
        
    for c in ransomNote:
        if not c in char_freq:
            return False
        char_freq[c] -= 1
        if char_freq[c] < 0:
            return False
        
    return True
```
{% endtab %}
{% endtabs %}
