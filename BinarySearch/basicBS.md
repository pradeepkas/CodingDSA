
with recursive apporoach

```swift
func BS(_ arr: [Int], target: Int,  s: Int, e: Int) -> Int {
    
    if s > e {
        return -1
    }
    
    let mid = (s + e) / 2
    
    if arr[mid] == target {
        return mid
    }
    
    if arr[mid] > target {
        return BS(arr, target: target, s: s, e: mid-1)
    }
    
    return BS(arr, target: target, s: mid+1, e: e)
}

```


SearchElementInRotatedSortedArray
