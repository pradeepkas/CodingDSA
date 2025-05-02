### Set Matrix Zero

```markdown
Input: matrix=[[0,1,2,0],[3,4,5,2],[1,3,1,5]]
Output:[[0,0,0,0],[0,4,5,0],[0,3,1,0]]
Explanation:Since matrix[0][0]=0 and matrix[0][3]=0. Therefore 1st row, 1st column and 4th column will be set to 0
```

## 1. brute force one 

```markdown
time :  O(n*m) * O(n+m) + O(n*m) ~= O(N*3)
space : O(1)
```

## 2. better one force one 

with extraa space and maintinning Int.Min at place of zeros

```swift
//[[1,1,1],[1,0,1],[1,1,1]]
    func setMatrixZero(_ matrix: inout [[Int]]) {
        guard !matrix.isEmpty, let numCols = matrix.first?.count else {
            print("Matrix is empty or invalid")
            return
        }

        let numRows = matrix.count
        print("Matrix dimensions: \(numRows) x \(numCols)")
        print("Initial matrix: \(matrix)")

        var zeroPositions: [(row: Int, col: Int)] = []

        // Step 1: Identify zeros and mark with Int.min
        for row in 0..<numRows {
            for col in 0..<numCols {
                if matrix[row][col] == 0 {
                    matrix[row][col] = Int.min
                    zeroPositions.append((row, col))
                }
            }
        }
        // O(N*M)

        // Step 2: Set corresponding rows and columns to zero
        for row in 0..<numRows {
            for col in 0..<numCols {
                if matrix[row][col] == Int.min {
                    zeroEntireRow(row, numCols)
                    zeroEntireColumn(col, numRows)
                }
            }
        }
        // (n * m) * (n+m)

        // Step 3: Restore Int.min back to 0
        for (row, col) in zeroPositions {
            matrix[row][col] = 0
        }

        print("Final matrix: \(matrix)")

        // Helper functions
        func zeroEntireRow(_ row: Int, _ cols: Int) {
            for col in 0..<cols {
                if matrix[row][col] != Int.min {
                    matrix[row][col] = 0
                }
            }
        }

        func zeroEntireColumn(_ col: Int, _ rows: Int) {
            for row in 0..<rows {
                if matrix[row][col] != Int.min {
                    matrix[row][col] = 0
                }
            }
        }
    }
```

will use cols and rows array as extraa for decision purpose 

```markdown
time :  O(n*m) + O(n*m) ~= O(n*m)
space : O(n+m) // extrra two arrays
```

```swift
func setMatricZeroOptimal(_ nums: inout [[Int]]) {
    let rows = nums.count
    let col = nums[0].count
    
    // extraa row and col for decision purpose
    var colD = Array(repeating: 1, count: col)
    var rowsD = Array(repeating: 1, count: rows)

    for i in 0..<rows {
        for j in 0..<col { //O(n*m)
            if nums[i][j] == 0 {
                rowsD[i] = 0
                colD[j] = 0
            }
        }
    }
    for i in 0..<rows { //O(n*m)
        for j in 0..<col {
            if rowsD[i] == 0 || colD[j] == 0  {
                nums[i][j] = 0
            }
        }
    }
}

```


## 3. optimal one 

avoid usage of extraa space as well by using extraa arrays in matrix it self