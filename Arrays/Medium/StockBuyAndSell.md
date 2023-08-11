## Stock Buy And Sell

```markdown
Input: prices = [7,1,5,3,6,4]
Output: 5
Explanation: Buy on day 2 (price = 1) and 
sell on day 5 (price = 6), profit = 6-1 = 5.

```

1. brute force 
check for every element

2. 

- traverse from last 
    - store max from last 
    - check for every element with current max




```swift
func maxProfit(_ prices: [Int]) -> Int {
    
    var last = prices.count - 1
    var currentMax = 0
    var profit = 0
     
    while(last >= 0) {
        let ele = prices[last]
        profit = max(currentMax - ele, profit)
        currentMax = max(ele, currentMax)
        
        last -= 1
    }
    return profit
}

```


![Alt text](/images_arr/stockbuySell.png)