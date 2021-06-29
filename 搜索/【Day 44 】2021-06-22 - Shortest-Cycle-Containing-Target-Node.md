## 题目地址：

https://binarysearch.com/problems/Shortest-Cycle-Containing-Target-Node



## 思路

图 bfs

看大佬解答 **[lilyzhaoyilu](https://github.com/lilyzhaoyilu)**



## 代码

JavaScript

```javascript
class Solution {
    solve(graph, target) {
       if(graph[target].length == 0) return -1
        
        const visited = new Set
        const queue = []
        
        for(const start of graph[target]){
            queue.push([start, 1])
        }

        while(queue.length){
            const [node, dis] = queue.shift()
            if(node == target) return dis
            if(visited.has(node)) continue
            visited.add(node)

            if(!graph[node]) continue
            for(const nei of graph[node]){
                queue.push([nei, dis + 1])
            }
        }

        return -1 
    }
}
```



## 复杂度

时间复杂度：O(V+ E)
空间复杂度：O(E)

