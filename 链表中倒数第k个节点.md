# 链表中倒数第K个结点

## 题目描述

输入一个链表，输出该链表中倒数第k个节点。为了符合大多数人的习惯，本题从1开始计数，即链表的尾节点是倒数第1个节点。

例如，一个链表有 6 个节点，从头节点开始，它们的值依次是 1、2、3、4、5、6。这个链表的倒数第 3 个节点是值为 4 的节点。

##  样例

```样例
给定一个链表: 1->2->3->4->5, 和 k = 2.

返回链表 4->5.
```

## 题解

![image-20220304215043580](https://gitee.com/Two_Fly/cloudimage/raw/master/img/image-20220304215043580.png)

若要求倒数第k个结点，则fast指针先走k步，若在循坏的过程中`fast==NULL`，只能说明k>链表长度，因为当k=链表长度时，虽然`fast==NULL`	，但是这次循坏`while(k--)`结束后是不会进入下次循坏的，若以`fast==NULL`的情况进入了循坏，说明k一定大于了链表的长度，故返回`NULL`

## 代码

```c++
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */


struct ListNode* getKthFromEnd(struct ListNode* head, int k){
    struct ListNode* fast=head;
    struct ListNode* slow=head;
    while(k--) 
    {
        if(fast==NULL) return NULL;
        fast=fast->next;
    }
    while(fast)
    {
        fast=fast->next;
        slow=slow->next;
    }
    return slow;
}
```

题目链接:

`[剑指 Offer 22. 链表中倒数第k个节点 - 力扣（LeetCode） (leetcode-cn.com)](https://leetcode-cn.com/problems/lian-biao-zhong-dao-shu-di-kge-jie-dian-lcof/)`

