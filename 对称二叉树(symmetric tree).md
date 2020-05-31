## 101.对称二叉树
给定一个二叉树，检查其是否是镜像对称的。
## 解：
* 1、递归
```
const check = (p, q) => {
  if(!p && !q) return true
  if(!p || !q) return false
  return p.val === q.val && (p.left, q.right) && (p.right, q.left)
}
const isSymmetric = (root) => {
  return check(root, root)
}
```
* 2、迭代算法
```
const isSymmetric = (root) => {
  let stack = [root, root]
  let p = root
  let q = root
  while (stack.length) {
    p = stack.shift()
    q = stack.shift()
    if(!p && !q) continue
    if((!p || !q) || p.val !== q.val) return false
    stack.push(p.left)
    stack.push(q.right)

    stack.push(p.right)
    stack.push(q.left)
  }
  return true
}
```