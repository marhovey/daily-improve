## 22.括号生成
数字n代表生成括号的对数，请你设计一个函数，用于能够生成所有可能的并且有效的括号

## 解：
* 1、递归
```
const generateParenthesis = (n) => {
  let res = []
  const gen = (left, right, str) => {
    if(left === n && right === n) return res.push(str)
    left < n && gen(left + 1, right, str + '(')
    right < left && gen(left, right + 1, str + ')')
  }
}
```