## Merge two Sorted Arrays Without Extra Space

```markdown
Input: 
n = 4, arr1[] = [1 4 8 10] 
m = 5, arr2[] = [2 3 9]

Output: 
arr1[] = [1 2 3 4]
arr2[] = [8 9 10]

```

## 1. sloutions 

```markdown
Time: (min(m,n) + nlogn + mlogm)
Space: O(1)
```

- swap all elemtns as shown in pic
- then sort both array

![Alt text](/images_arr/merge2SortedArr.png)


## 2. sloutions 

> will use shell sort 

in this will take gap for each iteration and tehn will swap element with gap only


```swift
func mergerTwoSortedArray(_ n1: inout [Int], n2: inout [Int] ) {
    
    let len = n1.count + n2.count
    var gap = (len / 2) + (len % 2)
    
    var p1 = 0
    var p2 = 0
    while ( gap > 0 ) {
        print("Current gap \(gap)")
        p1 = 0
        p2 = p1 + gap
        while ( p2 < (n1.count + n2.count - 1) ) {
            
            if getElement(p1) > getElement(p2) {
                swapForTwo(p1, p2: p2)
            }
            
            p1 += 1
            p2 += 1
        }
        if (gap == 1) {break} // to breakdown infinit loop
        gap = (gap / 2) + (gap % 2)
    }
    
    func swapForTwo(_ p1: Int, p2: Int) {
        
        let temp = getElement(p1)
        
        if p1 < n1.count && p2 < n1.count { 
            // its in first one
            n1[p1] = n1[p2]
            n1[p2] = temp
        }
        else if p1 >= n1.count && p2 >= n1.count {
            // its in second one
            n2[p1 - n1.count] = n2[p2]
            n2[p2] = temp
        } else {
            // its in both one
            n1[p1] = getElement(p2)
            n2[ p2 - n1.count ] = temp
        }
    }

    func getElement(_ index: Int) -> Int {
        if index < n1.count {
            return n1[index]
        } else {
            return n2[ index - n1.count ]
        }
    }
}
```


https://takeuforward.org/data-structure/merge-two-sorted-arrays-without-extra-space/
