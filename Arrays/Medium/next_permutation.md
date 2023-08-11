###



1. brute force   
n! * n someting, its taking a lot time


2. optimal 


## Optimal 

have to find breakpoint as you can see after 5 there is 1 means going down so its breakpoint for this 

![Alt text](/images_arr/nextPermutaion.png)


```swift
func nextPermuation(_ nums: inout [Int]) -> [Int] {
    
    var breakpoint = nums.count - 1
    var currentMin = -1

    // find first breakpoint menas ladder break
    while( breakpoint >= 0 ) {
        let ele = nums[breakpoint]
        
        if ele < currentMin {
            currentMin = ele
            break
        } else {
            currentMin = ele
        }
        
        breakpoint -= 1
    }
    
    print("got the brekpount for \(nums) == \(breakpoint)")
    // if not exist then return nums as revered one
    // 3,2,1 will 1,2,3
    if currentMin == -1 {
       nums = nums.reversed()
       return
    }
    
    // replace in remaining portion with breapoint
    var newlast = nums.count - 1
    while( newlast > breakpoint ) {
        let ele = nums[newlast]
        
        if ele > currentMin {
            nums.swapAt(breakpoint, newlast)
            break
        }
        newlast -= 1
    }
    print("replaced with breakpoint and smallest min \(nums) == \(breakpoint)")

    //reverse brekpoint + 1 to last
    reverseArr(breakpoint+1, end: nums.count-1 )
    
    print("reversed remaining arr \(nums)")
    func reverseArr(_ start: Int, end: Int) {
        var start = start
        var end = end
        while (start <= end){
            nums.swapAt(start, end)
            start += 1
            end -= 1
        }
    }
}

```

```markdown
Example o/p :
got the breakpoint index for [2, 1, 5, 4, 3, 0, 0] == 1
replaced with breakpoint and smallest min [2, 3, 5, 4, 1, 0, 0] == (3 to 1)
reversed remaining arr [2, 3, 0, 0, 1, 4, 5]
[2, 3, 0, 0, 1, 4, 5]

```