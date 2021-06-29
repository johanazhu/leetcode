## 题目地址：

https://leetcode-cn.com/problems/lian-biao-zhong-dao-shu-di-kge-jie-dian-lcof/



## 思路

链表

看到链表就应该想到快慢指针

当快指针 fast 走了k步后慢指针 slow 开始走

当快指针 fast 走出时，此时的 slow 位置即为链表中倒数第 k 个节点



## 代码

JavaScript

```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
/**
 * @param {ListNode} head
 * @param {number} k
 * @return {ListNode}
 */
var getKthFromEnd = function(head, k) {
    let slow = fast = head;
    while(fast) {
        fast = fast.next

        if (k-- <=0) {
            slow = slow.next;
        }
    }
    return slow
};
```



## 复杂度

时间复杂度：O(n)

空间复杂度：O(n)