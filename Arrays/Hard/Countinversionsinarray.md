
## Count inversions in an array

```markdown
Input Format: N = 5, array[] = {5,3,2,1,4}
Result: 7
Explanation: There are 7 pairs (5,1), (5,3), (5,2), (5,4),(3,2), (3,1), (2,1) and we have left 2 pairs (2,4) and (1,4) as both are not satisfy our condition. 
```

## sloutions

1. Brute force one   

have run two loops that will check elements

```swift
func inversion_count(_ nums: [Int]) {
    var count = 0
    for i in 0..<nums.count {
        for j in i+1..<nums.count {
            if nums[i] > nums[j] {
                count += 1
            }
        }
    }
    print(count)
}
```

## 2.  with merge sort 
Everything will save just add more conidition to get count 

## Why merge sort : bcz we need two sorted array that's why we are using merge sort, as you can see in this pic 

![Alt text](/images_arr/inversioncount.png)



```swift
class MergeSortAlgo {
    
     init() {
            var arr = [5,3,2,1,4] //[10,5,20,15,25,30,40]
            let count = mergeSortDemo(&arr, start: 0, end: arr.count - 1)
            print(arr)
            print(count)
     }
        
    func mergeSortDemo(_ arr: inout [Int], start: Int, end: Int) -> Int {
            var count = 0 //--
            if start >= end {
                return count
            }
            
            let mid = (start + end) / 2
            count += mergeSortDemo(&arr, start: start, end: mid) //--
            count += mergeSortDemo(&arr, start: mid+1, end: end) //--
            count += mergeSortedArrays(&arr, start: start, end: end) //--
            
            return count //--
     }
        
    func mergeSortedArrays(_ arr: inout [Int],
         start: Int, end: Int) -> Int {
            var count = 0 //--
            let mid = (start + end) / 2
            let n1 = arr[start...mid]
            let n2 = arr[mid + 1...end]
            var finalArr = [Int]()
            
            var n1Count = start
            var n2Count = mid + 1
            
            print("n1 \(n1)")
            print("n2 \(n2)")

            while (n1Count <= mid && n2Count <= end) {
                if n1[n1Count] > n2[n2Count] {
                    count += mid - n1Count + 1 //--
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
            return count
        }
}
```
