## Quick Sort

```markdown
time: O(nlogn)
space: O(1)   
```

## simple with starting pivot 

```swift
func mainQuickSort(_ num: inout [Int], low: Int, high: Int ) {
    
    if low < high {
        let part = quickSortPartitiion(&num, low: low, high: high)
        
        mainQuickSort(&num, low: low, high: part - 1)
        mainQuickSort(&num, low: part + 1, high: high)
    }
    print(num)
}

func quickSortPartitiion(_ num: inout [Int], low: Int, high: Int ) -> Int {
    let x = num[low]
    var i = low
    var j = low + 1
    while (j < num.count) {
        if num[j] <= x {
            i += 1
            num.swapAt(i, j)
        }
        j += 1
    }
    num.swapAt(i, low)    
    return i
}

```


## select pivot with any with left and right

```swift
func quickSortMainNew(_ num: inout [Int], low: Int, high: Int ) {
    if low < high {
        let part = newParition(&num, low: low, high: high)
        quickSorteddd(&num, low: low, high: part - 1)
        quickSorteddd(&num, low: part + 1, high: high)
    }
    print(num)
}


func newParition(_ num: inout [Int], low: Int, high: Int ) -> Int {
    
    let pivot = num[low]
    var i = low
    var j = high
    
    while ( i < j ) {
        
        while ( i < high  && num[i] <= pivot) {
            i += 1
        }
        
        while( j > low && num[j] > pivot ) {
            j -= 1
        }
        
        if i < j {
            num.swapAt(i, j)
        }
    }
    num.swapAt(low, j)
    return j
}

```