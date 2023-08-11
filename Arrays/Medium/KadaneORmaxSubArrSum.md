## Kadane’s Algorithm : Maximum Subarray Sum in an Array

1. brute force with O(N*2)



## Kadane’s Algorithm and print sub array also

> if current sum < 0 then leave and take next element as new sum 


```swift
func kadaneAlgo(_ nums: [Int]) -> Int {
    
    var sum = 0
    var maxSum = Int.min
    var firstIndex = 0
    var lastIndex = 0
    var start = 0
    
    for index in 0..<nums.count {
        if sum == 0 {start = index} // if sum == 0 then we are startin means its starting postioin for max
        
        let ele = nums[index]
        sum += ele
        
        if sum > maxSum {
            firstIndex = start
            lastIndex = index
            maxSum = sum
        }
        
        if sum < 0 {
            sum = 0
        }
        
    }
    return maxSum
}

```
