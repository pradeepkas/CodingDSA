## Two Sum : Check if a pair with given sum exists in Array

```markdown
Input Format: N = 5, arr[] = {2,6,5,8,11}, target = 14  

Result: YES (for 1st variant)
       [1, 3] (for 2nd variant)   
       
Explanation: arr[1] + arr[3] = 14. So, the answer is “YES” for the first variant and [1, 3] for 2nd variant.
```

## we have three approach 

1. Brute force   
using two loops 

2. Using hashmap (best but will take extraa space)

3. Two pointers   
but in this we sorted array only 

## using Hashmap 

Complexity:  
time: O(N)  
space: O(N)


```swift
    func twoSum(_ nums: [Int], _ target: Int) -> [Int] {
        var dict = [Int: Int]()
        for index in 0..<nums.count {
            let ele = nums[index]
            
            if let firstIndex = dict[target - ele] {
                return [firstIndex, index]
            }  
            dict[ele] = index
        }
    }
```