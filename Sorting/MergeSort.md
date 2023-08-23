
## Merge sort

time: O(nlogn)
space: O(N)   
auxliary space

1. stable   
means elements order will not change after merge

2. nlogn   
with extraa space for auxilary array

```swift
init() {
        var arr = [10,5,20,15,25,30,40]
        mergeSortDemo(&arr, start: 0, end: arr.count - 1)
        print(arr)
    }
    
    func mergeSortDemo(_ arr: inout [Int], start: Int, end: Int) {
        
        if start >= end {
            return
        }
        
        let mid = (start + end) / 2
        mergeSortDemo(&arr, start: start, end: mid)
        mergeSortDemo(&arr, start: mid+1, end: end)
        mergeSortedArrays(&arr, start: start, end: end)
    }
    
    func mergeSortedArrays(_ arr: inout [Int],
     start: Int, end: Int) {
        
        let mid = (start + end) / 2
        let n1 = arr[start...mid]
        let n2 = arr[mid + 1...end]
        var finalArr = [Int]()
        
        var n1Count = start
        var n2Count = mid + 1
        
        while (n1Count <= mid && n2Count <= end) {
            if n1[n1Count] > n2[n2Count] {
                finalArr.append(n2[n2Count])
                n2Count += 1
            }else {
                finalArr.append(n1[n1Count])
                n1Count += 1
            }
        }
        
        while(n1Count <= mid) {
            finalArr.append(n1[n1Count])
            n1Count += 1
        }
        
        while(n2Count <= end) {
            finalArr.append(n2[n2Count])
            n2Count += 1
        }

        n2Count = 0
        for index in start...end {
            arr[index] = finalArr[n2Count]
            n2Count += 1
        }
    }

```