## Basics

1. Plaindrome with recursion 

```swift
func isPalindrome(_ str: String, start: Int, end: Int) -> Bool {

    if (start > end) {  // base case 
        return true
    }

    let left = str.index(str.startIndex, offsetBy: start)
    let right = str.index(str.startIndex, offsetBy: end)
        
    if start == end && str[right] == str[left] {
        return true
    } else if str[right] == str[left]  {
        return isPalindrome(str, start: start + 1, end: end - 1)
    } else {
        return false
    }
}
```

updated one with one pointer only 

```swift
func isPalindromeUpdate(_ str: String, start: Int) -> Bool {
    
    if (start >= str.count / 2) || str.isEmpty {
        return true
    }

    let left = str.index(str.startIndex, offsetBy: start)
    let right = str.index(str.startIndex, offsetBy: str.count - 1 - start)
    
    if str[right] != str[left] {
        return false
    }
    
    return isPalindromeUpdate(str, start: start + 1)
}

```