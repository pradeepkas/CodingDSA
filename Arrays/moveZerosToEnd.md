### moveZeroes
have to maintain orders of elements

>always try to make refactor sloution in small parts .... or try to make functions

## first sloutions

using pointer but evetyhing at in single loop

```swift
    func moveZeroes(_ nums: inout [Int]) {
      var currentIndex = -1
    for index in 0..<nums.count {
        if nums[index] == 0 {
            if currentIndex == -1 {
                currentIndex = index
            }
        } else {
            if currentIndex != -1 {
                nums.swapAt(currentIndex, index)
                currentIndex += 1
            }
        }
    }
    }
```

## second sloution 

>using pointer but first placing pointer at particular place or at first zero

>>means after this pointer will be at first zero

>> and then start loop from next element of this pointer 

`example` 
arr = [1 ,0 ,2 ,3 ,0 ,4 ,0 ,1]  
pointer = 1  
loop will start from 2


```swift
func moveZeroes(_ nums: inout [Int]) {
    var currentIndex = -1
    
    for index in 0..<nums.count {
        if nums[index] == 0 {
            currentIndex = index
            break
        }
    }
    if currentIndex == -1 { return }
    // and start loop from here means before that no zero 
    for index in currentIndex+1..<nums.count {
        if nums[index] != 0 {
            nums.swapAt(currentIndex, index)
            if currentIndex + 1 < nums.count { currentIndex += 1 }
        }
    }
}

```