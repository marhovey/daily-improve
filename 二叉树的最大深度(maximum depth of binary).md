## 104.二叉树的最大深度
给定一个二叉树，找出其最大深度。
二叉树的深度为跟节点到最远叶子节点的最长路径伤的节点树。
## 解：
* 1、递归
```
const maxDeep = (root) => {
  let res = 0
  const dfs = (deep, node) => {
    if(!node) return
    res = Math.max(res, deep + 1)
    dfs(deep + 1, node.left)
    dfs(deep + 1, node.right)
  }
  dfs(0, root)
  return res
}
```
* 2、迭代算法
```
const maxDeep = (root) => {
  let res = 0;
  let stack = [{node: root, deep: 0}]
  while(stack.length) {
    const curr = stack.pop()
    const node = curr.node
    if(node) {
      const nextDeep = curr.deep + 1
      res = Math.max(nextDeep, res)
      node.left && stack.push({node: node.left, deep: nextDeep})
      node.right && stack.push({node: node.right, deep: nextDeep})
    }
  }
  return res
}
```