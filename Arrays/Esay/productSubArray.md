

## 238. Product of Array Except Self

1. using prefix sum and suffix sum 
2. than simple multiply both elements at index 
3. and that's our result

``` markdown
Example 1:

Input: nums = [1,2,3,4]
Output: [24,12,8,6]
Example 2:

Input: nums = [-1,1,0,-3,3]
Output: [0,0,9,0,0]

```

```markdown
Input: nums = [1,2,3,4]
suffix = 24, 12, 8, 6
prefix = 24, 12, 4, 1
finalarr = suffix[i] * prefix(i)

```

```swift
func productExceptSelf(_ nums: [Int]) -> [Int] {
    
    var ans = [Int]()
    
    var prefixSum = [Int]()
    var suffix = [Int]()
    
    var currentMul = 1
    prefixSum.append(1)
    
    for i in 1..<nums.count {
        currentMul *= nums[i-1]
        prefixSum.append(currentMul)
    }
    
    currentMul = 1
    suffix.append(1)
    var index = nums.count - 2
    
    while index >= 0 {
        currentMul *= nums[index+1]
        suffix.append(currentMul)
        index -= 1
    }
    suffix = suffix.reversed()
    
    for index in 0..<nums.count {
        ans.append(suffix[index] * prefixSum[index])
    }
    
    print(ans)
    
    return ans
    
}

```