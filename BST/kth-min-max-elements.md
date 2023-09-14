## Kth largest/smallest element in Binary Search Tree


for smallest element

- do inOrder traversal bcz inorder traversal will give you sorrted array 

- now you can return kth value from array

- to avoid extraa array space you can use counter and return when its equal to counter 



```swift
var k = 0

func inOrderaTraversal(_ root: TreeNode?) {
    if root != nil {
        print(root?.val)
        k += 1
        if k == 3 {
            print("got it ")
            return
        }
        if root?.left != nil {
            inOrderaTraversal(root?.left)
        } else {
            inOrderaTraversal(root?.right)
        }
        
    } 
}

```
