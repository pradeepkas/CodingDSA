
## First and Last occurrence in a sorted array

```markdown
Input: nums = [5,7,7,8,8,10], target = 8
Output: [3,4]
Example 2:

Input: nums = [5,7,7,8,8,10], target = 6
Output: [-1,-1]
```


repeat same for first as well

```swift
    var start = 0
    var end = nums.count - 1
    
    var last = -1
    
    while ( start <= end ) {
        let mid = (start + end) / 2
        
        if nums[mid] == target {
            last = mid
            start = mid + 1
        } else if nums[mid] > target {
            end = mid - 1
        } else {
            start = mid + 1
        }
        
    }
```

## Count Occurrences in Sorted Array

calculate first and last occurence of that element and do calculate number of elements 


```markdown
Example 1:
Input: N = 7,  X = 3 , array[] = {2, 2 , 3 , 3 , 3 , 3 , 4}
Output: 4
Explanation: 3 is occurring 4 times in 
the given array so it is our answer.

```