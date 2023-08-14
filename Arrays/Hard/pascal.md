## Pascal's Triangle

```markdown
1
1 1
1 2 1
1 3 3 1
1 4 6 4 1
1 5 10 10 5 1
```

## to find element for given row and col 

simple is n-1Cr-1 combination 
 
example : row = 6 and col = 3    

will be (5 * 4) / (1 * 2) = 10


## to print given row  

```swift
func generatePascalRow(_ row: Int) {
    var res = [Int]()
    var ans = 1
    res.append(ans)
    for index in 1..<row {
        ans = ans * (row - index)
        ans = ans / index
        res.append(ans)
    }
    print(res)
}

```


![Alt text](/images_arr/pascal.png)
