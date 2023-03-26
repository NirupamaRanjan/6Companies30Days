
# Rotate List &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/rotate-list/)

```
Linked List
``` 
### Problem Statement 
Given the head of a linked list, rotate the list to the right by k places.

### Sample Input
```
head =[1,2,3,4,5]
```
### Sample Output
```
k =2

```

### Solution
```cpp
class Solution {
public:
    
    int sizef(ListNode*head){
        int ans=0;
        while(head!=NULL){
            ans++;
            head=head->next;
        }
        
        return ans;
    }
    
    
    ListNode* rotateRight(ListNode* head, int k) {
        
        if(head==NULL || head->next==NULL || k==0) return head;
        
         ListNode*p=head;
         ListNode*n=head;

         
         int l=sizef(head);

         if(k%l==0) return head; 
         k=k%l;
        
        
        for(int i=0;i<k;i++){
            n=n->next;
        }
        
        while(n->next!=NULL){
            p=p->next;
            n=n->next;
        }
        
        ListNode*p2=p->next;
        
        p->next=NULL;
        n->next=head;
         
        return p2;
    }
};
```