# 1. 两数之和

```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function(nums, target) {
    const map = {}
    for (let i = 0; i < nums.length; i++) {
        const other = target - nums[i]
        // 这里需要注意
        if (map[other] !== undefined) {
            return [map[other], i]
        }
        map[nums[i]] = i
    }
};
```
