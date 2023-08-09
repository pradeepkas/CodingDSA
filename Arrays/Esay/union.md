### union

given arrays are sorted

1. using hasmap 

2. using set 

3. two pointers


## two pointers approach 

```markdown
//1,2,3,4,5,6,7,8,9,10  
//2,3,4,4,5,11,12

Common Elements in arr1 and arr2  are:  2,3,4,5  
Distnict Elements in arr1 are : 1,6,7,8,9,10  
Distnict Elemennts in arr2 are : 11,12   
Union of arr1 and arr2 is {1,2,3,4,5,6,7,8,9,10,11,12} 
```

```swift
func unionTwoArr(n1: [Int], n2: [Int]) {
    
    var n1Counter = 0
    var n2Counter = 0
    
    var ansArr = [Int]()
    
    while ( n1Counter < n1.count && n2Counter < n2.count ) {
        if n1[n1Counter] == n2[n2Counter] {
            ansArr.append(n1[n1Counter])
            n1Counter += 1
            n2Counter += 1
        } else {
            if n1[n1Counter] < n2[n2Counter] {
                if (ansArr.last ?? 0) != n1[n1Counter]  {
                    ansArr.append(n1[n1Counter])
                }
                n1Counter += 1
            } else {
                if (ansArr.last ?? 0) != n2[n2Counter]  {
                    ansArr.append(n2[n2Counter])
                }
                n2Counter += 1
            }
        }
    }
    
  // add reminaing array alos check both n1 and n2 same as merging two sorted array
    print(ansArr)
}

```