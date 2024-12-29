

## Type of Sloving DP problems

1. Tabluation -- bottom up approach (in this we can start from o to n or n to 0)
2. memoization -- top down approach (in this also we can start from o to n or n to 0)

![alt text](/images_arr/DP/imageDP.png)


### SubProblem overlapping: 
meaning we are doing calculation for same problem again like in fibnaccio problem ... if see recursion tree for F(5) we dont need to calcuclate f(2) and f(3) .. and so on again .. because we are already calcualted ...


## Memoization (Recursion to memoization)
 - Tend to store the value of sub problem in map/Array

- Here we are using 'arr' to store results to avoid subproblem overlapping

Example for memoiztion for fibnaccio

 ```swift
 // 0 1 1 2 3 5 8
    var arr = Array(repeating: -1, count: 7)
    let res = dpFibnaccioProblem(6, dpArr: &arr)
    print("result \(res)")

 func dpFibnaccioProblem(_ n: Int, dpArr: inout [Int]) -> Int {
        if n <= 1 {
            return n
        }
        
        if dpArr[n] != -1 {
            return dpArr[n]
        }
        
        let res = dpFibnaccioProblem(n-1, dpArr: &dpArr) + dpFibnaccioProblem(n-2, dpArr: &dpArr)
        dpArr[n] = res
        return res
    }
 ```

#### Time and space complexity :
- Time: o(n)
- space : o(n) (recursion stack size) + o(n) (storing result)



## Tablutaion (recursion to tabluation)
- we will use arr to store results 

   ```swift
    var arrTab = Array(repeating: -1, count: 7)
    // setting base case in array
    arrTab[0] = 0
    arrTab[1] = 1

    let res2 = dpTab(6, dpArr: &arrTab)
    print("result \(res2)")

    func dpTab(_ n: Int, dpArr: inout [Int]) -> Int {
        for index in 2...n {
            dpArr[index] = dpArr[index-1] + dpArr[index-2]
        }
        
        return dpArr[n]
    }
   ```

#### Time and space complexity :
- Time: o(n)
- space : ~~o(n) (recursion stack size)~~ (not required as we are not using recursion stack) + o(n) (storing result)


### more space optimization 

![alt text](/images_arr/DP/image2.png)

 // 0 1  1 2 3 5 8
    
   ```swift
    func dpTabWithoutArray(_ n: Int) -> Int {
        
        var prev0 = 0
        var prev1 = 1
        
        var current = -1
        
        for _ in 2...n {
            current = prev0 + prev1
            prev0 = prev1
            prev1 = current
        }
        
        return current
    }
   ```
#### Time and space complexity :
- Time: o(n)
- space : ~~o(n) (recursion stack size)~~ (not required as we are not using recursion stack) ~~+ o(n) (storing result)~~ not requried as we are not using any more any array only few variables 