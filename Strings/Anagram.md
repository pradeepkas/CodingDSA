## 242. Valid Anagram

Given two strings s and t, return true if t is an anagram of s, and false otherwise.

An Anagram is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.


```markdown
Example 1:
Input: s = "anagram", t = "nagaram"
Output: true

Example 2:
Input: s = "rat", t = "car"
Output: false

Example 3:
Input: s = "a", t = "ab"
Output: false

```


```swift
func isAnagram(_ s: String, _ t: String) -> Bool {
    if s.count != t.count {
        return false
    }
    var tDict = [Character: Int]()
    for char in t {
        if let exist = tDict[char] {
            tDict[char] = exist + 1
        } else {
            tDict[char] = 1
        }
    }
    for char in s {
        if let exist = tDict[char] {
            tDict[char] = exist - 1
            if (exist - 1) == 0 {
                tDict[char] = nil
            }
        } else {
            return false
        }
    }
    return true
}
```