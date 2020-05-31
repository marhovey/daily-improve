### 94.二叉树的中序遍历
给定一个二叉树，返回它的中序 遍历。

### 解：
* 1、递归算法
```
const postorderTraversal = (root) => {
  let res = []
  var inorder = (node) => {
    if(!node) return
    node.left && inorder(node.left)
    node.right && inorder(node.right)
    res.push(node.val)
  }
  inorder(root)
  return res
}
```
* 2、迭代算法
```
const postorderTraversal = (root) => {
  let res = []
  let stack = [root]
  while(stack.length) {
    const curr = stack.pop()
    if(curr) {
      res.unshift(curr.val)
      stack.push(curr.left)
      stack.push(curr.right)
    }
  }
  return res
}
```