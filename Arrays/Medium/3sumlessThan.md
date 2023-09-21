## Count triplets with sum smaller than a given value

### grab second time

![Alt text](/images_arr/lessthantriplets.png)


## brute force 
O(N3)

```swift
func threeSomeWithLessThanSumProblem() {
    var nums = [5, 1, 3, 4, 7]
    var sorted = nums.sorted()
    // 1,3,4,5,7
    for index in 0..<sorted.count - 2 { 
        for i in index + 1..<sorted.count {
            for j in i + 1..<sorted.count {
                let currentSum12 = sorted[i] + sorted[j] + sorted[index]
                if currentSum12 < k {
                    print("found at \(sorted[index]) \(sorted[i])  \(sorted[j])")
                }
                if currentSum12 > 12 {
                    break
                }
            }
        }
    }
}

```

## optimized version with sorting 

1. first we have sort the data 
2. then pointer based approach 
3. and <= check for more data
4. (k-j) check please check SS

```swift
func threeSomeWithLessThanSumProblemOptimise() {
    var nums = [5, 1, 3, 4, 7]
    var sorted = nums.sorted()
    // 1,3,4,5,7
    var ans = 0
    var sum = 12    
    for index in 0..<sorted.count - 2{ 
        var j = index + 1
        var k = sorted.count - 1
        
        while j < k {
            let currentSum12 = sorted[j] + sorted[k] + sorted[index]
            if currentSum12 >= sum {
                k -= 1 
            } else {
                ans += (k - j)
                j += 1
            }
        }
    }
    print("total possible way \(ans)")
}

```