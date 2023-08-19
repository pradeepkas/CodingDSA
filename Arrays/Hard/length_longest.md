## Length of the longest subarray with zero Sum


its almost same as longestSubarray
--> Arrays/Esay/longestSubArray.md

it will follow prefix sum pattern


## sloutions
1. brute force 
two loops 

2. hashmap 

```swift
func getLongestSubArray(_ nums: [Int]) {
    
    var dict = [Int: Int]()
    var currentSum = 0
    var maxLength = 0
    
    for index in 0..<nums.count {
        currentSum += nums[index]
        if currentSum == 0 {
            maxLength = index + 1
            continue
        }
        if let exist = dict[currentSum] {
            let len = index - exist //index - (exist + 1) + 1
            maxLength = max(maxLength, len)
        } else {
            dict[currentSum] = index
        }
    }
    print(maxLength)
}

```