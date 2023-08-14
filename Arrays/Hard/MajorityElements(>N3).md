## Majority Elements(>N/3 times) | Find the elements that appears more than N/3 times in the array


what will be the possiblties 

```markdown
n = 8
florr [n/3] = 2 (asking > means at least 3 times has to come this element)
so only only two element can exist

n = 10
florr [n/3] = 3 (asking > means at least 4 times has to come this element)
so only only two element can exist
```

## Sloutions 

1. brute force
2. hashmap (consider have to return at >n/3)
3. moore's couting enchaced verion

## Extended Boyer Moore’s Voting Algorithm

```swift
func mooreCounting(_ nums: [Int]) {
    var c1 = 0
    var ele1 = Int.min
    var c2 = 0
    var ele2 = Int.min
    
    for ele in nums {
        if c1 == 0 && ele != ele2 {
            c1 = 1
            ele1 = ele
        }
        else if c2 == 0 && ele != ele1 {
            c2 = 1
            ele2 = ele
        }
        else if ele1 == ele { c1 += 1 }
        else if ele2 == ele { c2 += 1 }
        else {
            c1 -= 1
            c2 -= 1
        }
    }
    c1 = 0
    c2 = 0
    let limit:Int = Int(floor(Double(nums.count/3)))
    for ele in nums {
        if ele == ele1  { c1 += 1 }
        if ele == ele2 { c2 += 1 }
    }
    if c1 > limit {
        print(ele1)
    }
    
    if c2 > limit {
        print(ele2)
    }
}
```


![Alt text](/images_arr/N3elments.png)


