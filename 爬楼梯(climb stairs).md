## 70.爬楼梯
假设你正在爬楼梯。需要n阶你才能到达楼顶。每次你可以爬1或2个台阶。你有多少种不同的方法可以到达楼顶
## 解：
* 1、普通递归
```
const climbStairs = (n) => {
  if(n < 3) return n
  const climb_stairs = (i, n) => {
    if( i > n) return 0
    if(i === n) return 1
    return climb_stairs(i+1, n) + climb_stairs(i + 2, n)
  }
  return climb_stairs(0, n)
}
```
* 2、记忆化递归
```
const climbStairs = (n) => {
  if(n < 3) return n
  let temp = []
  const climb_stairs = (i, n) => {
    if( i > n) return 0
    if(i === n) return 1
    if(temp[i]) return temp[i]
    temp[i] = climb_stairs(i+1, n) + climb_stairs(i + 2, n)
    return temp[i]
  }
  climb_stairs(0, n)
}
```
* 3、动态规划
```
const climbStairs = (n) => {
  if(n < 3) return n
  let temp = [0, 1, 2]
  let i = 3;
  while(i <= n) {
    temp[i] = temp[i - 1] + temp[i - 2]
  }
  return temp[n]
}
```