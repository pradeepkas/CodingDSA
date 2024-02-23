## missingNumber

## most important point is number range is `0 to n`


## summation apporach 
- simple one is   
- calculate sum from 0 to n with n(n+1)/2   
 - and then minus actual arr eleements sum 

```swift
    func missingNumber(_ nums: [Int]) -> Int {
        var sum = 0
        for ele in nums {
            sum += ele 
        }
        let finalSum = (nums.count * (nums.count + 1)) / 2 
        return finalSum - sum
    }
```

## xor appraoch 

> XOR of two same numbers is always 0 i.e. a ^ a = 0. ←Property 1.

> XOR of a number with 0 will result in the number itself i.e. 0 ^ a = a.  ←Property 2

```markdown
Assume the given array is: {1, 2, 4, 5} and N = 5.  
XOR of (1 to 5) i.e. xor1 = `(1^2^3^4^5)`   
XOR of array elements i.e. xor2 = `(1^2^4^5)`   
XOR of xor1 and xor2 = `(1^2^3^4^5) ^ (1^2^4^5)`  
			= `(1^1)^(2^2)^(3)^(4^4)^(5^5)`  
			= `0^0^3^0^0 = 0^3 = 3.`  
The missing number is 3.
```