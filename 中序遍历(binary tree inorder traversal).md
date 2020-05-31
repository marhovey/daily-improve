### 94.二叉树的中序遍历
给定一个二叉树，返回它的中序 遍历。

### 解：
* 1、递归算法
```
const inorderTraversal = (root) => {
  let res = []
  var inorder = (node) => {
    if(!node) return
      node.left && inorder(node.left)
      res.push(node.val)
      node.right && inorder(node.right)
  }
  inorder(root)
  return res
}
```
* 2、迭代算法
```
const inorderTraversal = (root) => {
  let res = []
  let stack = []
  let curr = root
  while(stack.length || curr !== null) {
    while (curr !== null) {
      stack.push(curr)
      curr = curr.left
    }
    curr = stack.pop()
    res.push(curr.val)
    curr = curr.right
  }
  return res
}
```