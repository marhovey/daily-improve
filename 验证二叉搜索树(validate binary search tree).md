## 98.验证二叉搜索树
给定一个二叉树，判断其是否是一个有效的二叉搜索树。
假设一个二叉搜索树具有如下特征：
* 节点的左子树只包含小于当前节点的数。
* 节点的右子树只包含大于当前节点的数。
* 所有的左子树和右子树自身必须是二叉搜索树

## 解：
* 1、递归法。(有效的二叉搜索树，中序遍历时应该是有序的)
```
const isValidBST = (root) {
  let res = true
  let curr = -Infinity
  let DFS = (node) {
    if(!node) return
    DFS(node.left)
    if(node.val <= curr) return res = false
    curr = node.val
    DFS(node.right)
  }
  DFS(root)
  return res
}
```
* 迭代算法
```
const isValidBST = (root) {
  let stack = []
  let curr = root
  let last = -Infinty
  while(curr !== null || stack.length) {
    while(curr) {
      stack.push(curr)
      curr = curr.left
    }
    curr = stack.pop()
    if(curr.val <= last) {
      return false
    }
    last = curr.val
    curr = node.right
  }
  return true
}
```