
## Longest Substring Without Repeating Characters

```markdown
Input: s = "abcabcbb"
Output: 3
Explanation: The answer is "abc", with the length of 

"aabaab!bb"
Output: 3

```


```swift
func longest(_ s: String) -> Int {
    var dict = [Character: Int]()
    var start = 0
    var longet = 0 
    
    for (index, char) in s.enumerated() {
        
        if let exist = dict[char] {
            start = max(exist + 1, start)
        } 
        longest = max(longet, index - start + 1)
        dict[char] = index
    }
    return longest
} 

```

```swift
    func lengthOfLongestSubstring(_ s: String) -> Int {
        let dataArr = Array(s)
        if dataArr.isEmpty || dataArr.count == 1 {
            return dataArr.count
        }
        var positionTracker = [String: Int]()
        var startPosition = 0
        var currentlen = 0
        
        for index in 0..<dataArr.count {
            let ele = "\(dataArr[index])"
            if let existIndex = positionTracker[ele] {
                currentlen = max(index - startPosition, currentlen) // 5
                startPosition = max(existIndex + 1, startPosition)
            } 
            positionTracker[ele] = index
        }
        currentlen = max(((dataArr.count) - startPosition), currentlen)
        return currentlen
    }

```