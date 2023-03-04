# Reverse Linked List II &ensp;   [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/reverse-linked-list-ii/)

```
Linked List
``` 
### Problem Statement 

Given the head of a singly linked list and two integers left and right where left <= right, reverse the nodes of the list from position left to position right, and return the reversed list.

### Sample Input
```
head = [1,2,3,4,5], left = 2, right = 4
```
### Sample Output
```
[1,4,3,2,5]
```

### Solution
```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* reverseBetween(ListNode* head, int left, int right) {
        if(head==NULL || head->next==NULL || left==right) return head;

        ListNode*c=head;
        ListNode*p=NULL;
        
        int count=1;
        
        while(count!=left){
            p=c;
            c=c->next;          
            count++;
        }
        
        if(p) p->next=NULL;
        
        ListNode*r=NULL;
        ListNode*rt=NULL;
        ListNode*n=c->next;
        
        while(c!=NULL && count<=right){
              if(r==NULL){
                 r=c;
                 r->next=NULL;
                 rt=r;
              }else{
                 c->next=r;
                 r=c;
              }
            
              c=n;
              if(n) n=n->next;
              count++;
        }
        
        rt->next=c;
        if(p) p->next=r;
     
        if(p) return head;
        return r;
        
    }
};
