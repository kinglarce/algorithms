# Group Anagrams

#### Links:

Group Anagrams -[ ](https://leetcode.com/problems/maximum-subarray/)[https://leetcode.com/problems/group-anagrams/](https://leetcode.com/problems/group-anagrams/)

#### Problem:

Given an array of strings `strs`, group **the anagrams** together. You can return the answer in **any order**.

An **Anagram** is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

**Example 1:**

```
Input: strs = ["eat","tea","tan","ate","nat","bat"]
Output: [["bat"],["nat","tan"],["ate","eat","tea"]]
```

#### Solutions

{% tabs %}
{% tab title="HashSet Chars Count - O(n)" %}
{% hint style="success" %}
Time: O(nk), Space: O(n)
{% endhint %}

{% hint style="info" %}
**Hint:**&#x20;
{% endhint %}

```python
 def groupAnagrams(strs: List[str]) -> List[List[str]]:
    anagrams = {}
    
    for word in strs:
        frequency = [0]*26
        for ch in word:
            frequency[ord(ch)-ord('a')] += 1
    
        key = tuple(frequency)
            
        if key not in anagrams:
            anagrams[key] = []
            
        anagrams[key].append(word)
        
    return anagrams.values()
```
{% endtab %}
{% endtabs %}
