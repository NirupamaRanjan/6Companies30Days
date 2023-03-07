# Remove Linked List Elements &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/remove-linked-list-elements/description/)

```
Linked List
``` 
### Problem Statement 
Given the head of a linked list and an integer val, remove all the nodes of the linked list that has Node.val == val, and return the new head.


### Sample Input
```
head = [1,2,6,3,4,5,6], val = 6
```
### Sample Output
```
[1,2,3,4,5]
```

### Solution
```cpp
class Solution {
public:
    ListNode* removeElements(ListNode* head, int val) {
        if(head==NULL) return head;

         while(head && head->val==val){
             head=head->next;
        }

        ListNode* present=head;
        ListNode* prev=NULL;

       
        while(present){
            if(present->val==val){
                ListNode* temp=present->next;
                if(prev) prev->next=temp;
                present->next=NULL;
                present=temp;
            }
           else{
               prev=present;
               present=present->next;
           } 
          
        }
        
        return head;

    }
};