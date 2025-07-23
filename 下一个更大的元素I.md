# [下一个更大的元素I](https://leetcode.cn/problems/next-greater-element-i/description/)

题目已知：不存在重复元素，那么我们可以对 `nums2` 进行遍历，找到其每个元素对应的下一个更大的元素（使用单调栈），然后存在哈希表中，再对 `nums1` 遍历，在哈希表中找对应的值即可

```js
var nextGreaterElement = function (nums1, nums2) {
    const result = new Array(nums1.length).fill(-1)
    const stack = []
    const map = new Map()
    for (let i = 0; i < nums2.length; i++) {
        while (i !== 0 && nums2[i] > stack[stack.length - 1]) {
            const popVal = stack.pop()
            map.set(popVal, nums2[i])
        }
        stack.push(nums2[i])
    }
    for(let i =0;i<nums1.length;i++){
        if(map.has(nums1[i])){
            result[i] = map.get(nums1[i])
        }
    }
    return result
};
```

时间复杂度：O(n)

空间复杂度：O(n)