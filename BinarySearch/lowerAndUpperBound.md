## lower bound 

> minimum index like this arr[index] >= target

```markdown
Example 2:
Input Format: N = 5, arr[] = {3,5,8,15,19}, x = 9
Result: 3
Explanation: Index 3 is the smallest index such that arr[3] >= x.
```

```swift
func lowerBound(_ arr: [Int], target: Int,  s: Int, e: Int) -> Int {
    var start = s
    var end = e
    
    var ans = arr.count
    
    while (start <= end) {
        
        let mid = (start + end) / 2
            
        if arr[mid] >= target {
            end = mid - 1
            ans = mid
        } else {
            start = mid + 1
        }
        
    }
    return ans
} 
```

## upper bound 

> minimum index like this arr[index] > target

```markdown
Example 2:
Input Format: N = 6, arr[] = {3,5,8,9,15,19}, x = 9
Result: 4
Explanation: Index 4 is the smallest index such that arr[4] > x.
```

```swift
func lowerBound(_ arr: [Int], target: Int,  s: Int, e: Int) -> Int {
    var start = s
    var end = e
    
    var ans = arr.count
    
    while (start <= end) {
        
        let mid = (start + end) / 2
            
        if arr[mid] > target { // just equal chagne
            end = mid - 1
            ans = mid
        } else {
            start = mid + 1
        }
        
    }
    return ans
} 
```


##  Search Insert Position


Problem Statement: You are given a sorted array arr of distinct values and a target value x. You need to search for the index of the target value in the array.

If the value is present in the array, then return its index. Otherwise, determine the index where it would be inserted in the array while maintaining the sorted order.

```markdown
Example 1:
Input Format: arr[] = {1,2,4,7}, x = 6
Result: 3
Explanation: 6 is not present in the array. So, if we will insert 6 in the 3rd index(0-based indexing), the array will still be sorted. {1,2,4,6,7}.

Example 2:
Input Format: arr[] = {1,2,4,7}, x = 2
Result: 1
Explanation: 2 is present in the array and so we will return its index i.e. 1.

```

> will use lower bound sloution arr[index] >= target

## Floor and Ceil in Sorted Array


What is the floor of x?
The floor of x is the largest element in the array which is smaller than or equal to x( i.e. largest element in the array <= x). 
--> ## put this condition in lower or upper bound

What is the ceiling of x?
The ceiling of x is the smallest element in the array greater than or equal to x( i.e. smallest element in the array >= x).




