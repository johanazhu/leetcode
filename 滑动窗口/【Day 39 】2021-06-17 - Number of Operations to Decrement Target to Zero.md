## 题目地址：

https://binarysearch.com/problems/Number-of-Operations-to-Decrement-Target-to-Zero



## 思路

滑动窗口

看 **[lilyzhaoyilu](https://github.com/lilyzhaoyilu)** 写的

这题看解题思路能看明白

这道题的意思是给你一个数组，你只可以移除数组两端的数。求最小移除次数，使得移除的数字和为 target。



## 代码

JavaScript

```javascript
class Solution {
    solve(nums, target) {
        // 如果target为0，那么直接返回0就是
        if (target === 0) return 0;
		// 将 nums 中的值都加起来
        let sum = 0;
        for (const n of nums) {
            sum += n;
        }
        let res = nums.length * 2;
		// 得到滑动窗口的总值
        const windowTarget = sum - target;
        // 判断windowTarget的两种异常情况
        if (windowTarget === 0) return nums.length;
        else if (windowTarget < 0) return -1;
		// 快慢指针
        for (let fast = 0, slow = 0, curSum = 0; fast < nums.length; fast++) {
            // 快指针当前值相加总和
            curSum += nums[fast];
            // 当快指针当前值相加大于滑动窗口总值且慢指针小于mus的长度
            while(curSum >= windowTarget && slow < nums.length) {
                // 如果正好相等，获取从快指针到慢指针的长度
                if (curSum === windowTarget) {
                    res = Math.min(nums.length - 1 - fast + slow, res)
                }
                // 如果不相等，说明太大，先减去慢指针当前值，并让慢指针往前走一步
                curSum -= nums[slow]
                slow++
            }
        }
        return res === nums.length * 2 ? -1 : res
    }
}
```



### 复杂度

时间复杂度：O(N)
空间复杂度：O(1)