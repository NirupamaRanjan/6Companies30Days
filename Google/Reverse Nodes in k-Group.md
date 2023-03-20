
# Reverse Nodes in k-Group &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/reverse-nodes-in-k-group/)

```
Linked List
``` 
### Problem Statement 
Given the head of a linked list, reverse the nodes of the list k at a time, and return the modified list.

k is a positive integer and is less than or equal to the length of the linked list. If the number of nodes is not a multiple of k then left-out nodes, in the end, should remain as it is.

You may not alter the values in the list's nodes, only nodes themselves may be changed.
 

### Sample Input
```
head = [1,2,3,4,5], k = 2
```
### Sample Output
```
[2,1,4,3,5]
```

### Solution
```cpp
class Solution {
    
    int length(ListNode*head){
          if(head==NULL) return 0;
           return 1+length(head->next);
    }
  
public:
    ListNode* reverseKGroup(ListNode* head, int k) {
        int l=length(head);
        
        ListNode* th=NULL;
        ListNode*tl=NULL;
        ListNode*oh=NULL;
        ListNode* ot=NULL;
        ListNode*c=head;
        
        while(l>=k){
            for(int i=0;i<k;i++){
                
                ListNode*f=c->next;
                c->next=NULL;
                
                if(th==NULL){
                    tl=c;
                    th=c;
                }else{
                     c->next=th;
                     th=c;
                }
               c=f;
            }
            
             if(oh==NULL)
             {
                    oh=th;
                    ot=tl;
            }else
             {   ot->next=th;
                 ot=tl;
              }
            
            th=NULL;
            tl=NULL;
            l-=k;
        }
        
           ot->next=c; 
    
        
        return oh;
    }
};
```