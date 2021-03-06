# 11. 盛最多水的容器

```javascript
/**
 * @param {number[]} height
 * @return {number}
 */
var maxArea = function(height) {
    // 对撞指针：寻找最大面积
    let left = 0, right = height.length - 1, max = 0
    while (left < right) {
        max = Math.max(max, (right - left)*Math.min(height[left], height[right]))
        // 向着更高的方向移动
        if (height[left] <= height[right]) {
            left++
        } else {
            right--
        }
    }
    return max
};
```
