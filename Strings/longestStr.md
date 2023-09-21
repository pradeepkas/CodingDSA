
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