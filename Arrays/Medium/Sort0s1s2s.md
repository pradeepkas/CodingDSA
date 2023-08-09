## Sort an array of 0s, 1s and 2s

We have three approachs 

1. using hashmap 
store occrucen of number and then add back in array with help count

2. sort function 

3. Ducth notation national Algorithm


## 3. Ducth notation national Algorithm

![Alt text](/images_arr/imageducthnotation.png)

we will work with three pointers `low, mid and high`

```swift
func sortColors(_ nums: inout [Int]) {
    var low = 0
    var mid = 0
    var high = nums.count - 1
    while( mid <= high) {
        
        if nums[mid] == 0 {
            nums.swapAt(mid, low)
            mid += 1
            low += 1
        }
        
        else if nums[mid] == 1 {
            mid += 1
        }
        
        else if nums[mid] == 2 {
            nums.swapAt(mid, high)
            high -= 1
        }
    }          
}

```

