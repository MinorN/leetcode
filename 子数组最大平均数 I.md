# [子数组最大平均数 I ](https://leetcode.cn/problems/maximum-average-subarray-i/)

定长的范围，求最大值，使用滑动窗口，先求出第一个最大值，从 0-k 的最大值，然后不断往右滑动，每次加上新值，减去开头的值即可

```js
var findMaxAverage = function (nums, k) {
    const n = nums.length
    let sum = 0
    for (let i = 0; i < k; i++) {
        sum += nums[i]
    }
    let maxSum = sum
    for (let i = k; i < n; i++) {
        sum = sum + nums[i] - nums[i - k]
        maxSum = Math.max(maxSum, sum)
    }


    return maxSum / k
};
```

