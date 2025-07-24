# [两数之和 II - 输入有序数组](https://leetcode.cn/problems/two-sum-ii-input-array-is-sorted/)

首先分析题目关键点：**非递减序列**，当然如果使用暴力方法可以解决问题，但是复杂度太高，我们思考一下，如果两个值加起来大于我们的目标值，我们就得减少，反之，小于目标值，就得加大对应的数

按照这个思想，我们使用双指针，一个指向头，一个指向结尾，会出现三种情况

1. 加起来正好等于目标值，直接返回下标（注意+1）
2. 加起来大于目标值，说明数取大了，那么我们移动尾指针，就可以减小
3. 加起来小于目标值，说明数取小了，那么我们移动头指针，就可以增大

```js
var twoSum = function (numbers, target) {
    const n = numbers.length
    let start = 0
    let end = n - 1
    while (start < end) {
        const result = numbers[start] + numbers[end] 
        if (result === target) {
            // 找到了对应的值
            return [start + 1, end + 1]
        }
        if(result > target){
            // 说明加的结果大于目标值
            // 那么就需要减小和，故而移动右指针，让 end 对应的值变小
            end--
        }else if(result < target){
            // 说明加的结果小于目标值
            // 需要增加，移动左指针
            start++
        }
    }
    return []
};
```

