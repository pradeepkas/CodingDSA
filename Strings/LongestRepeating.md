## Longest Repeating Character Replacement


## using sliding window

- we have to find all unique element and store in dict with 0
- now we will traverse string from 0 and will check if the current range is possible means its less than <=k 
- take max from current window


```markplace
Input: s = "ABAB", k = 2
Output: 4
Explanation: Replace the two 'A's with two 'B's or vice versa.
Example 2:

Input: s = "AABABBA", k = 1
Output: 4
```

```swift
func longestSeqWithWindow(_ s: String, k: Int) {
    var dict = [Character: Int]()
    for char in s {
        dict[char] = 0
    }    
    var left = 0
    var right = 0 
    var res = 0
    var arr = Array(s)
    
    for right in 0..<s.count {
        let charAtRight = arr[right]
        dict[charAtRight] =  (dict[charAtRight] ?? 0) + 1
        while (( right - left + 1 ) - maxFromDict(dict)) > k {
            let charAtLeft = arr[left]
            dict[charAtLeft] = (dict[charAtLeft] ?? 0) - 1
            left += 1
        }
        res = max(res, right - left + 1)
    }    
}

func maxFromDict(_ dict: [Character: Int]) -> Int {
    let values = dict.values
    return values.max() ?? 0
}

```
