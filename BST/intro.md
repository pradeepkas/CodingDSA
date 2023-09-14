
## intro for BST

```markdown
   N
 /    \ 
 L    R 
```

`L < N < R`  its general conditiion 

in most of the cases there will not `duplicates` but in some cases it may be then we can update like this `L <= N < R` or  `L < N <=  R`



## BST search 


```swift
func BSTSearch(_ root: TreeNode?, target: Int) -> TreeNode? {
    guard let root = root else {return nil}
    if root.val == target {
        return root
    }
    if root.val > target {
        return BSTSearch(root.left, target: target)
    } else {
        return BSTSearch(root.right, target: target)
    }
}

```

## Ceil in a Binary Search Tree

means find val for key(given) like this `val >= key`

recursion One

```swift
var ceil = -1

func findCeilRecusion(_ root: TreeNode?, _ key: Int) -> Int {
    guard let root = root else {return ceil}
    
    if root.val == key {
        return root.val
    }
    
    if root.val > key {
        ceil = root.val
        return findCeil(root.left, key)
    } else {
        return findCeil(root.right, key)
    }
}

```

without recursion simple one

```swift
func findCeil(_ root: TreeNode?, _ key: Int) -> Int {
    // conddition that we have to find  val >= key
    var ceilIn = -1
    var root = root
    while( root != nil ) {
        if (root!.val) == key {
            return root!.val
        }
        if root!.val > key {
            ceilIn = root!.val
            root = root?.left
        } else {
            root = root?.right
        }
    }
    return ceilIn
}
```



## Floor in a Binary Search Tree

means find val for key(given) like this `val <= key`


```swift
func findFloor(_ root: TreeNode?, _ key: Int) -> Int {
    // conddition that we have to find val <= key
    var ceilIn = -1
    var root = root
    while( root != nil ) {
        
        if (root!.val) == key {
            return root!.val
        }

        if root!.val > key {
            root = root?.left
        } else {
            ceilIn = root!.val
            root = root?.right
        }
    }
    return ceilIn
}

```


## insert node in tree 

