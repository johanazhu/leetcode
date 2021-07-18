## 题目地址：

https://leetcode-cn.com/problems/fei-bo-na-qi-shu-lie-lcof/



## 思路

递归可以，但是会超时

用动态规划是正道



## 代码

JavaScript

```javascript
/**
 * @param {number} n
 * @return {number}
 */
var fib = function(n) {
    let n1 = 0, n2 = 1, sum;
    for (let i = 0; i < n; i++) {
        sum = (n1 + n2) % 1000000007;
        n1 = n2;
        n2 = sum;
    }
    return n1
};
```



## 复杂度

时间复杂度：O(n)

空间复杂度：O(n)