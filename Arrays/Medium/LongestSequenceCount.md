
## Longest Consecutive Sequence in an Array

```markdown
Example 1:
Input: [100, 200, 1, 3, 2, 4]
Output: 4
Explanation: The longest consecutive subsequence is 1, 2, 3, and 4.
```

### 1. First approach is with sorted array and count 
```markdown
time : O(N) + O(nlogn)
space : O(1)
```

```swift
//[100,1,2,100,101,102,100,3,4,3]
func longestConsecutiveSeq(_ nums: [Int]) {
    var nums = nums.sorted()
    var currentCount = 1
    var currentNumber = nums[0]
    var maxSeq = 1
    
    for index in 1..<nums.count {
        if nums[index] == currentNumber {
            continue
        }
        if nums[index] - 1 == currentNumber {
            currentCount += 1
            currentNumber = nums[index]
        } else {
            currentCount = 1
            currentNumber = nums[index]
        }
        maxSeq = max(maxSeq,currentCount)
    }
    print(maxSeq)
}
```


### 2. using set 

```markdown
time : O(N) + O(N) + O(2N) = ~ O(N)
space : O(N)
```

![Alt text](/images_arr/longestSeq.png)

```swift
func longestConsecutive(_ nums: [Int]) -> Int {
    var arrSet = Set<Int>()
    for ele in nums {  //// O(N)
        arrSet.insert(ele)
    }
    var currentLeng = 0
    
    for ele in arrSet {  //// O(N)
        if !arrSet.contains(ele - 1) {
            var seq = ele
            var counter = 0
            while (arrSet.contains(seq)) { /// not for all so cant say (n*n) bcz in total it will run only 2N times 
                seq += 1
                counter += 1
            }
            currentLeng = max(currentLeng,counter)
        }
    }
    return currentLeng
}

``` 
