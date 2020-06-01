## 31.下一个排列
实现获取下一个排列的函数，算法需要将给定数字序列重新排列成字典序中下一个更大的排列。
如果不存在下一个更大的排列，则将数字重新排列成最小的排列（即升序排列）。
必须原地修改，只允许使用额外常数空间。
## 解：
* 1、从后面开始寻找第一个a[i]比a[i-1]大的位置。如果不存在则不存在下一个更大的排列。如果存在，则找到第一个比a[i-1]大的数a[j]，将a[j]的位置与a[i-1]互换，最后把a[i]以后的数排列即可。
```
const nextPermutaion = (nums) {
  let i = nums.length - 2
  while(i >=0 && nums[i] > nums[i+1]) {
    i--
  }
  if(i >= 0) {
    let j = nums.length - 1;
    while(j >= 0 && nums[j] <= nums[i]) {
      j--
    }
    swap(nums, i, j)
  }
  reverse(nums, i + 1)
}
const swap = (nums, i, j) => {
  const temp = nums[j]
  nums[j] = nums[i]
  nums[i] = temp
}
const reverse = (nums, i) => {
  let j = nums.length - 1
  while(i < j) {
    swap(nums, i, j)
    i++
    j--
  }
}
```