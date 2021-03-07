# 15. 三数之和

```javascript
/**
 * @param {number[]} nums
 * @return {number[][]}
 */
var threeSum = function(nums) {
    // 1、找出数组中三个元素之后=0
    // 2、三元组并且不可以重复
    // 3、先排序 + 双指针
    const answer = []
    if (!nums || !Array.isArray(nums) || nums.length <= 2) {
        return answer
    }
    nums.sort((a, b) => a - b)
    for (let i = 0; i < nums.length; i++) {
        // 去除不必要的比较：优化比较次数
        if (nums[i] > 0) {
            return answer
        }
        // 跳过重复的比较
        if (i > 0 && nums[i] === nums[i-1]) {
            continue
        }
        // 双指针
        let left = i + 1
        let right = nums.length - 1
        while (left < right) {
            if (nums[i] + nums[left] + nums[right] === 0) {
                answer.push([nums[i], nums[left], nums[right]])
                while (left < right && nums[left] === nums[left + 1]) {
                    left += 1
                }
                while (left < right && nums[right] === nums[right - 1]) {
                    right -= 1
                }
                left += 1
                right -= 1
            } else if (nums[i] + nums[left] + nums[right] > 0) {
                right -= 1
            } else {
                left += 1
            }
        }
    }
    return answer
};
```
