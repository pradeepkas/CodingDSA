## singleNumber
measns single occurence,  all other elements will be there twice.

example:   
[4,1,2,1,2]  
ans : 4

1. using hashmap
2. using set
3. using XOR 

## USING XOR

> ←Property 1: XOR of two same numbers is always 0 i.e. `a ^ a = 0`. 

> ←Property 2: XOR of a number with 0 will result in the number itself i.e. `0 ^ a = a`.

```swift
    func singleNumber(_ nums: [Int]) -> Int {
        var xor = 0
        for ele in nums {
            xor = xor ^ ele 
        }
        return xor
    }
```