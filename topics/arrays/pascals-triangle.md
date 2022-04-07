# Pascal's Triangle

#### Links:

Pascal's Triangle -[ ](https://leetcode.com/problems/maximum-subarray/)[https://leetcode.com/problems/pascals-triangle/](https://leetcode.com/problems/pascals-triangle/)

#### Problem:

Given an integer `numRows`, return the first numRows of **Pascal's triangle**.

In **Pascal's triangle**, each number is the sum of the two numbers directly above it as shown:

![](https://upload.wikimedia.org/wikipedia/commons/0/0d/PascalTriangleAnimated2.gif)

&#x20;

**Example 1:**

```
Input: numRows = 5
Output: [[1],[1,1],[1,2,1],[1,3,3,1],[1,4,6,4,1]]
```

#### Solutions

{% tabs %}
{% tab title="DP - O(n^2)" %}
{% hint style="success" %}
Time: O(n^2), Space: O(1) - Space doesn't come towards storage of `numRows`.
{% endhint %}

{% hint style="info" %}
**Hint:** Create each row placeholder with `num+1` since the loop would start from `0`.

Then set end-to-end `row[0]` and `row[-1]` to `1` .

Loop in the middle and get value from previous row value, that is `triangle[num-1][j-1]` and `triangle[num-1][j]` and sum it up for current row `row[j]`.&#x20;
{% endhint %}

```python
def generate(numRows: int) -> List[List[int]]:
    triangle = []
    
    for num in range(numRows):
        row = [0]*(num+1)
        row[0], row[len(row)-1] = 1, 1
        
        for j in range(1, len(row)-1):
            row[j] = triangle[num-1][j-1] + triangle[num-1][j]
            
        triangle.append(row)
    
    return triangle
```
{% endtab %}
{% endtabs %}
