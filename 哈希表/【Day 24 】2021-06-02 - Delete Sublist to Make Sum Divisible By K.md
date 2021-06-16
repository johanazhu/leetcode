## 题目地址：

https://binarysearch.com/problems/Delete-Sublist-to-Make-Sum-Divisible-By-K



## 思路

hash Table 做不出来

贴上 **[lilyzhaoyilu](https://github.com/lilyzhaoyilu)** 的解题



## 代码

JavaScript

```javascript
var minSubarray = function(nums, p) {
       const memo = new Map()
        let shortestLength = nums.length;
        let sum = 0
        for(const num of nums){
            sum += num
        }
        const targetMod = sum % p

        if(targetMod == 0) return 0
        let presum = 0

        //为了应对例子[1,2] p = 2,也就是当i = 0 且要删除自己的时候。
        memo.set(0,-1)
        for(let i = 0; i < nums.length; i++){
            presum += nums[i]
            let curMod = presum % p
            memo.set(curMod, i)
            if(memo.has((curMod - targetMod + p) % p)){
                shortestLength = Math.min(shortestLength, i - memo.get((curMod - targetMod + p) % p))
            }
        }
        return shortestLength == nums.length ? -1 : shortestLength
};
```



## 复杂度

时间复杂度：O(N)
空间复杂度：O(N)

