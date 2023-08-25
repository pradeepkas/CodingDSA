## Count Reverse Pairs

merge sort with extra countPair function to check this 

inititutionon is same as counterinversion problem 


```swift
class MergeSortAlgoforPari {
    
    //var count = 0
    init() {
        var arr = [2,4,3,5,1] //[10,5,20,15,25,30,40]
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
        count += countPair(&arr, start: start, end: end)
        mergeSortedArrays(&arr, start: start, end: end) //--
        
        return count //--
    }
    
    func countPair(_ arr: inout [Int], start: Int, end: Int) -> Int {
        var count = 0 //--
        let mid = (start + end) / 2
        let n1 = arr[start...mid]
        let n2 = arr[mid + 1...end]
        var n2Count = mid + 1
        
        for index in start...mid {
            
            while( n2Count <= end && n1[index] > (2*n2[n2Count]) ) {
                n2Count += 1
            }
            count += n2Count - (mid + 1)
        }
        
        return count
        
    }
    
    func mergeSortedArrays(_ arr: inout [Int], start: Int, end: Int) {
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
    
}

```