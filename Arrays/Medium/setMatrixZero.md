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

```swift
//[[1,1,1],[1,0,1],[1,1,1]]
func setMatricZero(_ nums: inout [[Int]]) {
    let rows = nums.count
    let col = nums[0].count
    print(nums)
    for i in 0..<rows { // O(n*m)
        for j in 0..<col {
            if nums[i][j] == 0 {
                setStarForRow(i) //O(n+m)
                setStarForCol(j)
            }
        }
    }
    //print(nums)
    func setStarForRow(_ row: Int) {
        for index in 0..<col {
            if nums[row][index] != 0 {
                nums[row][index] = -1
            }
        }
    }
    func setStarForCol(_ col: Int) {
        for index in 0..<rows {
            if nums[index][col] != 0 {
                nums[index][col] = -1
            }
        }
    }
    // at last now replace -1 to 0 as well 
    //O(n*m)
}

```


## 2. better one force one 

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