## Traversal

```markdown
inorder : LNR
preorder: NLR
postorder: LRN
```


```swift
func inOrderPrint(_ root: Tree?) {
    if root != nil {
        inOrderPrint(root?.leftNode)
        print(root?.data ?? 0)
        inOrderPrint(root?.rightNode)
    }
}
```


```swift
func inorderTraversal(_ root: TreeNode?) -> [Int] {
        
    if root?.left == nil && root?.right == nil {
        let val = root?.val == nil ? [] : [root?.val ?? 0]
        return val
    }
    
    let data = root?.val == nil ? [] : [root?.val ?? 0]
    let l1 = inorderTraversal(root?.left)
    let right = inorderTraversal(root?.right)

    return l1 +  data +  right
}

```

## level Order Traversal 

```swift
Input: root = [3,9,20,null,null,15,7]
Output: [[3],[9,20],[15,7]]
```

```swift
func isArrEmpty(_ arr: [[TreeNode]]) -> Bool {
    let main = arr.count
    let first = arr.first?.count
    if first == 0 {
        return true
    }
    return false
}


func levelOrder(_ root: TreeNode?) -> [[Int]] {
    var ans = [[Int]]()
    var arr = [[TreeNode]]()
    
    if root == nil {
        return ans
    }
    
    arr.append([root!])
    
    while (!isArrEmpty(arr)) {
        let first = arr.removeFirst()
        var temp = [TreeNode]()
        var tempData = [Int]()
        
        for ele in first {
            if let left = ele.left {
                temp.append(left)
            }
            if let right = ele.right {
                temp.append(right)
            }
            tempData.append(ele.val)
        }
        arr.append(temp)
        ans.append(tempData)
    }
    
    return ans
}

```