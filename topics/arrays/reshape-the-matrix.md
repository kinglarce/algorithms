# Reshape the Matrix

#### Links:

Reshape the Matrix - [https://leetcode.com/problems/reshape-the-matrix/](https://leetcode.com/problems/reshape-the-matrix/)

#### Problem:

You are given an `m x n` matrix `mat` and two integers `r` and `c` representing the number of rows and the number of columns of the wanted reshaped matrix.

The reshaped matrix should be filled with all the elements of the original matrix in the same row-traversing order as they were.

If the `reshape` operation with given parameters is possible and legal, output the new reshaped matrix; Otherwise, output the original matrix.

**Example 1:**

```
Input: mat = [[1,2],[3,4]], r = 1, c = 4
Output: [[1,2,3,4]]
```

#### Solutions

{% tabs %}
{% tab title="Queue - O(m*n)" %}
{% hint style="success" %}
Time: O(m\*n), Space: O(m\*n)
{% endhint %}

{% hint style="info" %}
**Hint:** Have a Queue which in this case is `q` , then we pop each value in front which we'll push it to `result` , but instead of using the matrix row and column length, we use the `r` and `c` which is the input that matches the boundaries of the placeholder `result`.

Validate if the `r` and `c` boundaries doesn't exceeds to the matrix `mat` row and columns lengths.&#x20;
{% endhint %}

```python
def matrix_reshape(mat: List[List[int]], r: int, c: int) -> List[List[int]]:
    # Validate if expected col and row match to boundaries of matrix
    if not mat or (r * c != len(mat) * len(mat[0])): 
        return mat
    
    result = [[0 for _ in range(c)] for _ in range(r)]
    q = []
    
    for i in range(len(mat)):
        for j in range(len(mat[i])):
            q.append(mat[i][j])
            
    for i in range(r):
        for j in range(c):
            result[i][j] = q.pop(0)
            
    return result
```
{% endtab %}

{% tab title="Row by Row - O(m*n)" %}
{% hint style="success" %}
Time: O(m\*n), Space: O(m\*n)
{% endhint %}

{% hint style="info" %}
**Hint:** Same idea as the Queue, but instead, we keep track of the `row` and `col` and check if `col` is equal to the expected column boundary which is `c` then we restart the `col` and increase the `row` so that `mat[i][j]` value goes to next row.

Validate if the `r` and `c` boundaries doesn't exceeds to the matrix `mat` row and columns lengths.&#x20;
{% endhint %}

```python
def matrix_reshape(self, mat: List[List[int]], r: int, c: int) -> List[List[int]]:
    # Validate if expected col and row match to boundaries of matrix
    if not mat or (r * c != len(mat) * len(mat[0])): 
        return mat
    
    result = [[0 for _ in range(c)] for _ in range(r)]
    row, col = 0, 0
    
    for i in range(len(mat)):
        for j in range(len(mat[i])):
            result[row][col] = mat[i][j]
            col += 1
            
            if col == c:
                row += 1
                col = 0
            
    return result
```
{% endtab %}

{% tab title="Circular Index - O(m*n)" %}
{% hint style="success" %}
Time: O(m\*n), Space: O(m\*n)
{% endhint %}

{% hint style="info" %}
**Hint:** Use division on row and modulus on column where `index // c` would give circular index of rows and `index % c` would give circular index of columns.

We need to keep a counter `index` which the `c` boundary would use for getting the index.

Validate if the `r` and `c` boundaries doesn't exceeds to the matrix `mat` row and columns lengths.&#x20;
{% endhint %}

```python
def matrixReshape(mat: List[List[int]], r: int, c: int) -> List[List[int]]:
    # Validate if expected col and row match to boundaries of matrix
    if not mat or (r * c != len(mat) * len(mat[0])): 
        return mat
    
    result = [[0 for _ in range(c)] for _ in range(r)]
    index = 0
    for i in range(len(mat)):
        for j in range(len(mat[i])):
            row_idx = index // c
            col_idx = index % c
            result[row_idx][col_idx] = mat[i][j]
            index += 1

    return result
```
{% endtab %}
{% endtabs %}
