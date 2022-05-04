# Valid Palindrome

#### Links:

Valid Palindrome - [https://leetcode.com/problems/valid-palindrome/](https://leetcode.com/problems/valid-palindrome/)

#### Problem:

A phrase is a **palindrome** if, after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters, it reads the same forward and backward. Alphanumeric characters include letters and numbers.

Given a string `s`, return `true` _if it is a **palindrome**, or_ `false` _otherwise_.

**Example 1:**

```
Input: s = "A man, a plan, a canal: Panama"
Output: true
Explanation: "amanaplanacanalpanama" is a palindrome.
```

#### Solutions

{% tabs %}
{% tab title="Two Pointer - O(n)" %}
{% hint style="success" %}
Time: O(n), Space: O(1)
{% endhint %}

{% hint style="info" %}
**Hint:** Run a `left` and `right` pointer where `left` is the starting point and `right` is the last index and compare each end if it's the same. While comparing, check if it's alphanumeric, if it's not, then just skip and adjust the pointers accordingly.
{% endhint %}

```python
def is_palindrome(s: str) -> bool:
    left, right = 0, len(s)-1
    
    while left < right:
        if not s[left].isalnum():
            left += 1
        elif not s[right].isalnum():
            right -= 1
        else:
            if s[left].lower() != s[right].lower():
                return False
            left += 1
            right -= 1
        
        
    return True
```
{% endtab %}

{% tab title="Reversal - O(n)" %}
{% hint style="success" %}
Time: O(n), Space: O(n)
{% endhint %}

{% hint style="info" %}
**Hint:** The key is to basically reverse the string and compare but before that, ensure you only get the alphanumeric, lower-case them all and then reverse.
{% endhint %}

```python
def is_palindrome(s: str) -> bool:
    filtered_chars = filter(lambda ch: ch.isalnum(), s)
    lowercase_filtered_chars = map(lambda ch: ch.lower(), filtered_chars)
    
    filtered_chars_list = list(filtered_chars)
    reversed_chars_list = filtered_chars_list[::-1]
    
    return filtered_chars_list == reversed_chars_list
```
{% endtab %}
{% endtabs %}
