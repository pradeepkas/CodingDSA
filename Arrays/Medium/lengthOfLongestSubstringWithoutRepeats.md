## Length of Longest Substring without any Repeating Character

https://takeuforward.org/data-structure/length-of-longest-substring-without-any-repeating-character/

Problem Statement: Given a String, find the length of longest substring without any repeating character.

Examples:

Example 1:

Input: s = ”abcabcbb”

Output: 3

Explanation: The answer is abc with length of 3.

Example 2:

Input: s = ”bbbbb”

Output: 1

Explanation: The answer is b with length of 1 units.



```swift
    func lengthOfLongestSubstringWithoutRepeat(_ s: String) -> Int {
        if s.isEmpty { return 0 }
        var maxLen = 0
        var lastSeenIndex = [Character: Int]()
        var windowStart = 0
        
        for (index, char) in s.enumerated() {
            if let existIndex = lastSeenIndex[char] {
                windowStart = max(existIndex + 1, windowStart)
            }
            lastSeenIndex[char] = index
            maxLen = max(maxLen, index - windowStart + 1)
        }
        
        return maxLen
    }

```    
