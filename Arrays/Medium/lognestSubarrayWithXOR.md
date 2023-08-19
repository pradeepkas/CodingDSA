## Count the number of subarrays with given xor K

```markdown
Pre-requisite: Find the number of subarrays with the sum K
```

```markdown
Example 1:
Input Format: A = [4, 2, 2, 6, 4] , k = 6
Result: 4
Explanation: The subarrays having XOR of their elements as 6 are  [4, 2], [4, 2, 2, 6, 4], [2, 2, 6], [6]
```

![Alt text](/images_arr/xorLongestSum.png)

```swift
func getLongestSubArrayWithXor(_ nums: [Int], k: Int) {
    
    var dict = [Int: Int]()
    var currentSum = 0
    var count = 0
    
    dict[0] = 1
    
    for index in 0..<nums.count {
        currentSum ^= nums[index]
        
        let check = currentSum ^ k
        count += dict[check] ?? 0
        
        if let exist = dict[currentSum] {
            dict[currentSum] = exist + 1
        } else {
            dict[currentSum] = 1
        }
    }
    print(count)
}

```
