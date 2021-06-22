## 题目地址：

https://binarysearch.com/problems/Top-View-of-a-Tree



## 思路

抄**[lilyzhaoyilu](https://github.com/lilyzhaoyilu)** 的

我是一个没有感情的复制工具



## 代码

JavaScript

```javascript
/**
 * class Tree {
 *   constructor(val, left=null, right=null) {
 *     this.val = val
 *     this.left = left
 *     this.right = right
 *   }
 * }
 */
class Solution {
    solve(root) {
        if(!root) return []
        const view = new Map
        view.set(0, root.val)
        const queue = [[root,0]]

        while(queue.length){
            const [node, cor] = queue.shift()
            if(!view.has(cor)) view.set(cor, node.val)
            node.left && queue.push([node.left, cor -1])
            node.right && queue.push([node.right, cor + 1])
        }

        const res = [...view.entries()].sort((a,b) => a[0] -b[0])
        return res.map(([k,v]) => v) 
    }
}
```



### 复杂度

时间复杂度：O(NlogN) 搜索所有的点是O(n), 给map排序是o(nlogn)，遍历字典是O(n)
空间复杂度：O(N) memo和queue的大小

