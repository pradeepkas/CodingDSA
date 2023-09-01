## Minimum in Rotated Sorted Array

```markdown
Example 1:
Input Format: arr = [4,5,6,7,0,1,2,3]
Result: 0
Explanation: Here, the element 0 is the minimum element in the array.
```


```swift
func minimumInSortedRotateArray(_ nums: [Int]) {
    
    var start = 0
    var end = nums.count - 1
    
    var found = Int.max
    
    while( start <= end) {
        
        let mid =  ( start + end ) / 2
                
        //check for left one is sorted or not
        if nums[start] <= nums[mid] {
            found = min(nums[start], found)
            start = mid + 1
            
        } else { //right portion is  sorted then
            found = min(nums[mid], found)
            end = mid - 1
        }
    }
    print(found)    
}

```

## Find out how many times the array has been rotated

just find minimum element in sorted and rotated array index and return 

```swift
Example 1:
Input Format: arr = [4,5,6,7,0,1,2,3]
Result: 4
Explanation: The original array should be [0,1,2,3,4,5,6,7]. So, we can notice that the array has been rotated 4 times.

```

 minimum = 0 
 minIndex = 4

 answer is also 4 means 4 rotatation will take place to get this array
 