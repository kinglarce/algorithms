# Valid Parentheses

#### Links:

Valid Parentheses - [https://leetcode.com/problems/valid-parentheses/](https://leetcode.com/problems/valid-parentheses/)

#### Problem:

Given a string `s` containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`, determine if the input string is valid.

An input string is valid if:

1. Open brackets must be closed by the same type of brackets.
2. Open brackets must be closed in the correct order.

**Example 1:**

```
Input: s = "()[]{}"
Output: true
```

**Example 2:**

```
Input: s = "(]"
Output: false
```

#### Solutions

{% tabs %}
{% tab title="Stack - O(n)" %}
{% hint style="success" %}
Time: O(n), Space: O(n)
{% endhint %}

{% hint style="info" %}
**Hint:** Have a mapping in place for **opening parentheses** as the **key** and **closing parentheses** as the **value** in the dictionary.

The approach uses stack, push `char` if it's opening parentheses and pop if it's closing. Check the popped `top_char` if it matches to the `mapping[char].`
{% endhint %}

```python
def isValid(self, s: str) -> bool:
    mapping = {
        '(': ')',
        '{': '}',
        '[': ']'
    }
    stack = []
    
    for char in s:
        if char == '(' or char == '{' or char == '[':
            stack.append(char)
        else:
            if len(stack) == 0:
                return False
            top_char = stack.pop()
            if top_char != mapping[char]:
                return False
    
    return True if len(stack) == 0 else False
```
{% endtab %}
{% endtabs %}
