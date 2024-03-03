## 152. Maximum Product Subarray


```swift
Example 1:
Input: nums = [2,3,-2,4]
Output: 6
Explanation: [2,3] has the largest product 6.

Example 2:
Input: nums = [-2,0,-1]
Output: 0
Explanation: The result cannot be 2, because [-2,-1] is not a subarray.

arr = [3,2,-1,0,`5,4,2,-1,-5`,0,-5,-5]
ans = 200 (5,4,2,-1,-5)

```

## apporach 
1. will take two value for prefix and suffix mul 
2. and will from start and end at same time
3. will compare mul at each step 
4. will carry forward maximum from there



```swift
//let arr = [0,0,0,1,1,0,0,0]

//let arr = [-1, -2, -1, -1, -1]

func productSubarray() {
    
    var prefixMul = 1
    var suffixMul =  1
    
    var maxMul = Int.min
    
    for index in 0..<arr.count {
        
        if prefixMul == 0 {prefixMul = 1}
        if suffixMul == 0 {suffixMul = 1}
        
        prefixMul *= arr[index]
        suffixMul *= arr[arr.count - 1 - index]
        
        maxMul = max(maxMul, max(prefixMul, suffixMul))
    }
    
    print(maxMul)
}

```