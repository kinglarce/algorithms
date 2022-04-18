# Encode and Decode Strings

#### Links:

Encode and Decode Strings -[ ](https://leetcode.com/problems/maximum-subarray/)[https://leetcode.com/problems/encode-and-decode-strings/](https://leetcode.com/problems/encode-and-decode-strings/), [https://www.lintcode.com/problem/659/](https://www.lintcode.com/problem/659/)

#### Problem:

Design an algorithm to encode **a list of strings** to **a string**. The encoded string is then sent over the network and is decoded back to the original list of strings.

Machine 1 (sender) has the function:

```
string encode(vector<string> strs) {
  // ... your code
  return encoded_string;
}
```

Machine 2 (receiver) has the function:

```
vector<string> decode(string s) {
  //... your code
  return strs;
}
```

So Machine 1 does:

```
string encoded_string = encode(strs);
```

and Machine 2 does:

```
vector<string> strs2 = decode(encoded_string);
```

`strs2` in Machine 2 should be the same as `strs` in Machine 1.

Implement the `encode` and `decode` methods.

You are not allowed to solve the problem using any serialize methods (such as `eval`).

**Example 1:**

```
Input: dummy_input = ["Hello","World"]
Output: ["Hello","World"]
Explanation:
Machine 1:
Codec encoder = new Codec();
String msg = encoder.encode(strs);
Machine 1 ---msg---> Machine 2

Machine 2:
Codec decoder = new Codec();
String[] strs = decoder.decode(msg);
```

#### Solutions

{% tabs %}
{% tab title="Hashmap - O(n)" %}
{% hint style="success" %}
Time: O(n), Space: O(n) -&#x20;
{% endhint %}

{% hint style="info" %}
**Hint:** Quick solution is to join the array of strings with a delimiter but the edge case is that what if the string itself has the a delimiter that we used, then it's gonna be a problem. So for encoding, we combine the length of word plus the delimiter when we encode each word and place it on string.

e.g. 4#word -> 4 is length, "#" is delimeter, and finally "word".

For decoding, we will use two-pointer that is `i` and `j` and we move them accordingly when `j` find the delimiter which is `#.`
{% endhint %}

```python
 class Codec:
    def encode(self, strs: [str]) -> str:
        """Encodes a list of strings to a single string.
        """
        result = ""
        for word in strs:
            result += str(len(word)) + "#" + word
            
        return result

    def decode(self, s: str) -> [str]:
        """Decodes a single string to a list of strings.
        """
        result = []
        i = 0
        
        while i < len(s):
            j = i
            while s[j] != '#':
                j += 1
            
            word_len = int(s[i:j])
            word = s[j+1: j+word_len+1]
            result.append(word)
            i = j+word_len+1
            
        return result
```
{% endtab %}
{% endtabs %}
