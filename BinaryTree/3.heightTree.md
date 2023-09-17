


```swift
func heightForTree(_ root: TreeNode?) -> Int {
    if root == nil {
        return 0
    }
    
    if root?.left == nil && root?.right == nil {
        return 1
    }
    
    let left = heightForTree(root?.left)
    let right = heightForTree(root?.right)
    return 1 + max(left, right)
}

```