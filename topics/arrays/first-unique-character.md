# First Unique Character

#### Links:

First Unique Character in a String -[ ](https://leetcode.com/problems/maximum-subarray/)[https://leetcode.com/problems/first-unique-character-in-a-string/](https://leetcode.com/problems/first-unique-character-in-a-string/)

#### Problem:

Given a string `s`, _find the first non-repeating character in it and return its index_. If it does not exist, return `-1`.

**Example 1:**

```
Input: s = "asdfasxdf"
Output: 6
```

#### Solutions

{% tabs %}
{% tab title="Hashmap - O(n)" %}
{% hint style="success" %}
Time: O(n), Space: O(1) - English alphabet is fix 26 letters
{% endhint %}

{% hint style="info" %}
**Hint:** Get the frequency of characters then check who got the value `1.`
{% endhint %}

```python
from collections import Counter

def first_uniq_char(s: str) -> int:
    count = Counter(s)
    for i, char in enumerate(s):
        if count[char] == 1:
            return i
    
    return -1
```
{% endtab %}
{% endtabs %}
