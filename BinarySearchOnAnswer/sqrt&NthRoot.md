## Finding Sqrt of a number using Binary Search

Note: The question explicitly states that if the given number, n, is not a perfect square, our objective is to find the maximum number, x, such that x squared is less than or equal to n (x*x <= n). In other words, we need to determine the floor value of the square root of n.



```swift
func sqrtFind(_ num: Int) {
    
    var ans = Int.max
    var low = 1
    var high = num
    
    while( low <= high ) {
        
        let mid =  ( low + high ) / 2
        
        if mid * mid <= num {
            ans = mid
        }
        
        if mid * mid <= num {
            low = mid + 1
        } else {
            high = mid - 1
        }
    }
    
    print(high)
    print(ans)
    
}

```

```swift
func sqrtFind(_ num: Int) {
    var low = 1
    var high = num
    
    while( low <= high ) {
        
        let mid =  ( low + high ) / 2

        if mid * mid <= num {
            low = mid + 1
        } else {
            high = mid - 1
        }
    }
    
    print(high)
    
}

```


## Nth Root of a Number using Binary Search


```markdown
Example 1:
Input Format: N = 3, M = 27
Result: 3
Explanation: The cube root of 27 is equal to 3.

Example 2:
Input Format: N = 4, M = 69
Result: -1
Explanation: The 4th root of 69 does not exist. So, the answer is -1.

```

```swift
func NthRootFinder(_ num: Int, k: Int) -> Int {
    
    var low = 1
    var high = num
    
    while( low <= high ) {
        
        let mid =  ( low + high ) / 2
        
        let mul = getMul(mid, k: k)
        
        if mul == num {
            return mid
        }
                
        if mul <= num {
            low = mid + 1
        } else {
            high = mid - 1
        }
    }
    
    func getMul(_ i: Int, k: Int) -> Int {
        var mul = 1
        for _ in 1...k {
            mul *= i
        }
        return mul
    }
    return -1
    
}

```