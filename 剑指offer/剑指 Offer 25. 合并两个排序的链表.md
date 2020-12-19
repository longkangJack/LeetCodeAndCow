#### [剑指 Offer 25. 合并两个排序的链表](https://leetcode-cn.com/problems/he-bing-liang-ge-pai-xu-de-lian-biao-lcof/)

输入两个递增排序的链表，合并这两个链表并使新链表中的节点仍然是递增排序的。

**示例1：**

```
输入：1->2->4, 1->3->4
输出：1->1->2->3->4->4
```

```c++
//非递归方法
class Solution {
public:
    ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) {
        ListNode* head = new ListNode(0);
        ListNode* p = head;
        if(l1 ==nullptr)
        return l2;
        if(l2==nullptr)
        return l1;
        while(l1&&l2)
        {
            if(l1->val<l2->val)
            {
                p->next = l1;
                l1 = l1->next;
            }
            else
            {
                p->next = l2;
                l2 = l2->next;
            }
            p = p->next;
        }
        p->next = l1==nullptr?l2:l1;
        return head->next;
    }
};
//递归方法
class Solution {
public: 
    ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) {
        if(l1==nullptr)
        {
            return l2;
        }
        if(l2==nullptr)
        {
            return l1;
        }
        ListNode* head=new ListNode(0);
        if(l1->val<l2->val)
        {
            head=l1;
            head->next=mergeTwoLists(l1->next,l2);
        }
        else
        {
            head=l2;
            head->next=mergeTwoLists(l2->next,l1);
        }
        return head; 
    }
};
```

