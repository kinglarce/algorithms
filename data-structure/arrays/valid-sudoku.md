# Valid Sudoku

#### Links:

Valid Sudoku -[ ](https://leetcode.com/problems/maximum-subarray/)[https://leetcode.com/problems/valid-sudoku](https://leetcode.com/problems/valid-sudoku)

#### Problem:

Determine if a `9 x 9` Sudoku board is valid. Only the filled cells need to be validated **according to the following rules**:

1. Each row must contain the digits `1-9` without repetition.
2. Each column must contain the digits `1-9` without repetition.
3. Each of the nine `3 x 3` sub-boxes of the grid must contain the digits `1-9` without repetition.

**Note:**

* A Sudoku board (partially filled) could be valid but is not necessarily solvable.
* Only the filled cells need to be validated according to the mentioned rules.

**Example 1:**

![](https://upload.wikimedia.org/wikipedia/commons/thumb/f/ff/Sudoku-by-L2G-20050714.svg/250px-Sudoku-by-L2G-20050714.svg.png)

```
Input: board = 
[["5","3",".",".","7",".",".",".","."]
,["6",".",".","1","9","5",".",".","."]
,[".","9","8",".",".",".",".","6","."]
,["8",".",".",".","6",".",".",".","3"]
,["4",".",".","8",".","3",".",".","1"]
,["7",".",".",".","2",".",".",".","6"]
,[".","6",".",".",".",".","2","8","."]
,[".",".",".","4","1","9",".",".","5"]
,[".",".",".",".","8",".",".","7","9"]]
Output: true
```

#### Solutions

{% tabs %}
{% tab title="Hashset - O(n^2)" %}
{% hint style="success" %}
Time: O(n^2), Space: O(n^2)
{% endhint %}

{% hint style="info" %}
**Hint:** We use hashset where we'll record the rows, columns and 3x3 boxes if it doesn't have repetition.

For 3x3 boxes, we get the row index `i // 3` and column index `j // 3` to find out which 3x3 box it is.&#x20;

`Example 1: row` `8//3 is 2 and col 7//3 is 2, then the index of the box we'll be looking for is (2, 2) which is the last 3x3 box.`

`Example 2: row` 4`//3 is 1 and col 6//3 is 2, then the index of the box we'll be looking for is (1, 2) which is the middle-last 3x3 box.`
{% endhint %}

```python
import collections

def is_valid_sudoku(board: List[List[str]]) -> bool:
    rows = collections.defaultdict(set)
    cols = collections.defaultdict(set)
    boxes_of_3x3 = collections.defaultdict(set)
    
    for i in range(9):
        for j in range(9):
            val = board[i][j]
            
            if val is ".":
                continue
            
            # Check unique rows
            if val in rows[i]:
                return False
            rows[i].add(val)
            
            # Check unique columns
            if val in cols[j]:
                return False
            cols[j].add(val)
            
            # Check 3x3 boxes
            box_idx = (i // 3, j // 3)
            if val in boxes_of_3x3[box_idx]:
                return False
            boxes_of_3x3[box_idx].add(val)
            
    return True
```
{% endtab %}
{% endtabs %}
