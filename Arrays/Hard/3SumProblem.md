
## 3 Sum : Find triplets that add up to a zero

Problem Statement: Given an array of N integers, your task is to find unique triplets that add up to give a sum of zero. In short, you need to return an array of all the unique triplets [arr[a], arr[b], arr[c]] such that i!=j, j!=k, k!=i, and their sum is equal to zero.

```markdown
Input: nums = [-1,0,1,2,-1,-4]

Output: [[-1,-1,2],[-1,0,1]]

Explanation: Out of all possible unique triplets possible, [-1,-1,2] and [-1,0,1] satisfy the condition of summing up to zero with i!=j!=k

```

## Sloutions
## 1. brute force 
O(N3)

## 2. using hashmap or convert to 2 sum problem
Complexity:  
time: O(N2)  
space: O(N) for hashmap


```swift
func get3Sum(_ nums: [Int]) -> [[Int]] {
    var result = Set<[Int]>()
    for i in 0..<nums.count {
        let currentSum = -(nums[i]) // suppose 
        //(b+c) = -(a) so now you have to find (b+c) pair with -a sum
        var dict = [Int: Int]()
        for j in i+1..<nums.count {
            if i == j {continue}
            if let value = dict[currentSum - nums[j]] {
                addToSet([nums[i], nums[value], nums[j]])
            } else {
                dict[nums[j]] = j
            }
        }
    }
    return Array(result)
    func addToSet(_ arr: [Int]) {
        let arr = arr.sorted()
        result.insert(arr)
    }
}
```

## 3. Two pointer problem

in this we have to sort the array but we can avoid extraa space usage

----
```markdown
Complexity:  
time: O(Nlogn) +  O(N2)  ~= O(N2*logn)
space: O(1)   
//extraa only for answer strage not for algo
```
----

```swift
func getThreeSum(_ nums: [Int]) {
    
    let nums = nums.sorted()    
    var answer = Set<[Int]>()
    
    for i in 0..<nums.count - 2 {
        var j = i + 1
        var k = nums.count - 1
        while( j < k ) {
            let sum = nums[i] + nums[j] + nums[k]
            if sum < 0 {
                j += 1
            }
            if sum > 0 {
                k -= 1
            }
            if sum == 0 {
                addToSet([nums[i] , nums[j] , nums[k]])
                j += 1
                k -= 1
                while( j < k && nums[j] == nums[j-1]) { j += 1 } // to avoid taking againg same pair
                while( k < i && nums[k] == nums[k+1]) { k -= 1 }
            }
        }
    }
    print(answer)
    func addToSet(_ arr: [Int]) {
        let arr = arr.sorted()
        answer.insert(arr)
    }
}

```

![Alt text](/images_arr/3SumHard.png)