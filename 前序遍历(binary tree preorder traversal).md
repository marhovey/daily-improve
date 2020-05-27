## 144.二叉树的前序遍历
给定一个二叉树，返回他的前序遍历
## 解：
* 1、递归解法
```
const preorderTraversal = (root) => {
  let res = []
  let dfs = (node) => {
    if(!node) return
    res.push(node.val)
    node.left && dfs(node.left)
    node.right && dfs(node.right)
  }
  dfs(root)
  return res
}
```
* 2、队列解法（迭代算法）
```
const preorderTraversal = (root) => {
  let res = []
  let queue = [root]
  while(queue.length) {
    const curr = queue.unshift()
    curr && res.push(curr.val)
    curr && curr.right && queue.unshift(curr.right)
    curr && curr.left && queue.unshift(curr.left)
  }
}
```