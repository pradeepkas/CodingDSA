## Find the Majority Element that occurs more than N/2 times

we have three solutions 

1. brurte force 
array traversing for all elements 
O(N*2)

2. hashmap   
```markdown
time : O(N)
space : O(N)
```

3. Optimal Approach: Moore’s Voting Algorithm

## Moore’s Voting Algorithm

```swift
func majorityElements(_ nums: [Int]) -> Int {
    
    var counter = 0
    var currentElement = 0
    
    for ele in nums {
        if counter == 0 {
            counter = 1
            currentElement = ele
        } else if currentElement == ele {
            counter += 1
        } else {
            counter -= 1
        }
    }
    
    var counterForFound = 0
    for ele in nums {
        if currentElement == ele {
            counterForFound += 1
        }
    }
        
    if nums.count/2 < counterForFound {
        return currentElement
    }
    return -1
}
```


```markdown
1. Initialize 2 variables:
Count –  for tracking the count of element
Element – for which element we are counting
2. Traverse through the given array.
- If Count is 0 then store the current element of the array as Element.
- If the current element and Element are the same increase the Count by 1.
- If they are different decrease the Count by 1.
3. The integer present in Element should be the result we are expecting 

```