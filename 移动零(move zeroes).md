##283.移动零
给定一个数组nums，编写一个函数将所有的0移动到数组的末尾，同事保持非零元素的位置

##解：
1、开新数组，最后补齐0
const moveZeroes = (nums) => {
  let res = []
  const len = nums.length
  for(let i = 0; i < len; i++) {
    if(nums[i] !== 0) {
      res.push(nums[i])
    }
  }
  while(res.length < len) {
    res.push(0)
  }
  return res
}
2、记录下一个非零节点的位置
const moveZeroes = (nums) => {
  const len = nums.length
  let j = 0
  for(let i = 0; i < len; i++) {
    if(nums[i] !== 0) {
      nums[j] = nums[i]
      if(i !== j) {
        nums[j] = 0
      }
      j++
      continue
    }
  }
  return nums
}