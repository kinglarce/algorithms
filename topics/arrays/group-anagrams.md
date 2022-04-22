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
{% tab title="HashMap Chars Count - O(n)" %}
{% hint style="success" %}
Time: O(n\*k), Space: O(n) - n is length of list, k is max length of string.
{% endhint %}

{% hint style="info" %}
**Hint:** Since the key to anagram is using the letter exactly once, then we just need to group together the words with the same letters. &#x20;

Create a `hashmap/dict` with `key` using the frequency of letters on each word in `strs` and an array value where we can just push each word if the frequency of letters already exists in the `hashmap`.

`[0]*26` ? Is the placeholder for the frequency of letter use in the word since there are only 26 letters in the alphabet.

`ord(ch)-ord('a')` ? `ord` function grabs the ASCII unicode value of the character and we subract with a fixed unicode value of `ord('a')` which is 97.

e.g. `ord('b') - ord('a')` would equal to 1 since "b" unicode value is 98 and "a" unicode value is 97.&#x20;
{% endhint %}

```python
 def group_anagrams(strs: List[str]) -> List[List[str]]:
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

{% tab title="Iterative w/ Sorting  -  O(n * k log k)" %}
{% hint style="success" %}
Time: O(n \* k log k), Space: O(n)
{% endhint %}

{% hint style="info" %}
**Hint:**&#x20;
{% endhint %}

```python
 def groupAnagrams(self, strs):
 ans = collections.defaultdict(list)
 for s in strs:
     ans[tuple(sorted(s))].append(s)
 return ans.values()
```
{% endtab %}
{% endtabs %}
