## Tranpose of matrix

row to col and col to row
![Alt text](/images_arr/tranpose.png)

```swift
func transposeMatrix(_ matrix: inout [[Int]]) {
    let rows = matrix.count
    let col = matrix[0].count
    for i in 0..<rows {
        for j in i..<col { // will not start from zero
            let temp = matrix[i][j]
            matrix[i][j] = matrix[j][i]
            matrix[j][i] = temp
        }
    }
}
```
```markdown
i/p == [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
o/p == [[1, 4, 7], [2, 5, 8], [3, 6, 9]]
```

## Rotate Image by 90 degree

```markdown
Example 1:
Input: [[1,2,3],[4,5,6],[7,8,9]]
Output: [[7,4,1],[8,5,2],[9,6,3]]
Explanation: Rotate the matrix simply by 90 degree clockwise and return the matrix.
```
1. first do transpose 
2. then reveser every row 


## Rotate Matrix anti-clockwise by 90 degree

```markdown
Example 1:
Input:   {{1,2,3},
          {4,5,6},
          {7,8,9}}
Output:
        3 6 9 
        2 5 8 
        1 4 7 
Explanation: Rotate the matrix anti-clockwise by 90 degrees and return it.
```
1. first do transpose 
2. then reveser every col 
