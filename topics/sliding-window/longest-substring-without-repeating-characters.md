# Longest Substring Without Repeating Characters

#### Links:

Longest Substring Without Repeating Characters - [https://leetcode.com/problems/longest-substring-without-repeating-characters/](https://leetcode.com/problems/longest-substring-without-repeating-characters/)

#### Problem:

Given a string `s`, find the length of the **longest substring** without repeating characters.

**Example 1:**

```
Input: s = "abcabcbb"
Output: 3
Explanation: The answer is "abc", with the length of 3.
```

**Example 2:**

```
Input: s = "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.
```

#### Solutions

{% tabs %}
{% tab title="Brute Force - O(n^3)" %}
{% hint style="success" %}
Time: O(n^3), Space: O(n)
{% endhint %}

{% hint style="info" %}
**Hint:**  Run a `left` and `right` pointer where `right` pointer run through the rest of the string while checking if the character already exists. If it exists, reset the `right` pointer and adjust the `left` pointer to move forward.
{% endhint %}

```python
def length_of_longest_substring(s: str) -> int:
    longest = 0
    
    for left in range(len(s)):
        longest_str = ""
        
        for right in range(left, len(s)):
            char = s[right]
            
            if char not in longest_str:
                longest_str += char
                longest = max(longest, right - left + 1)
            else:
                break
                
    return longest
```
{% endtab %}

{% tab title="Sliding Window - O(n)" %}
{% hint style="success" %}
Time: O(n), Space: O(n)
{% endhint %}

{% hint style="info" %}
**Hint:**  There are 3 main logic for this approach, have a `dict/hashmap` to basically track what has been seen and what's the last index of it, check the duplicate character which is what we use `max()` on line 9 to know if it's the same character then we adjust the `left` and get the longest substring by getting the delta of `right` and `left` pointer.

Line 9 is where we adjust the longest substring pointer because that character exists in the `seen.`
{% endhint %}

```python
def length_of_longest_substring(s: str) -> int:
    seen = {}
    longest = 0
    left = 0
    
    for right in range(len(s)):
        char = s[right]
        if char in seen:
            left = max(left, seen.get(char) + 1)
            
        seen[char] = right
        longest = max(longest, right - left + 1)
        
    return longest
```
{% endtab %}
{% endtabs %}
