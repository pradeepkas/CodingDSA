## Merge Overlapping Sub-intervals


```markdown
Input: intervals=[[1,3],[2,6],[8,10],[15,18]]
Output: [[1,6],[8,10],[15,18]]

Explanation: Since intervals [1,3] and [2,6] are overlapping we can merge them to form [1,6]
 intervals.
```

## sloutions 

1. brute force 

run two loops and check every pair and merge 


2. sorting and checking 

```swift
func merge(_ arr: [[Int]]) -> [[Int]] {
       if arr.count == 1 {
            return arr
        }
    // sorting 
      arr = arr.sorted(by: { a, b in
        if a.first! < b.first! {
            return true
        } else if a.first! == b.first! {
            return a.last! < b.last!
        }
        return false
    })       
    // answer array      
    var tempArr = [[Int]]()
    tempArr.append(arr[0])
    
    for index in 1..<arr.count {
        
        var prev = tempArr.removeLast()
        var current = arr[index]
        
        if current[0] <= prev[1] {
            prev[1] = max(prev[1], current[1])
            tempArr.append(prev)
        } else {
            tempArr.append(prev)
            tempArr.append(current)
        }
    }
    return tempArr
}
```

```swift
    func merge(_ intervals: [[Int]]) -> [[Int]] {
        if intervals.isEmpty { return [] }
        let sortedIntervals = intervals.sorted(by: { $0[0] < $1[0] })

        var result = [sortedIntervals[0]]
        
        for index in 1..<sortedIntervals.count {
            let current = sortedIntervals[index]
            let last = result.last!
            if last[1] >= current[0] {
                result[result.count - 1][1] = max(last[1], current[1])
            } else {
                result.append(current)
            }
        }
        print(result)
        return result
    }

```

![Alt text](/images_arr/pairMerging.png)