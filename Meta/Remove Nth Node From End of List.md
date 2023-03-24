
# Remove Nth Node From End of List &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/remove-nth-node-from-end-of-list/description/)

```
Linked List
``` 
### Problem Statement 
Given the head of a linked list, remove the nth node from the end of the list and return its head.

### Sample Input
```
head = [1,2,3,4,5], n = 2
```
### Sample Output
```
[1,2,3,5]
```

### Solution
```cpp
class Solution {
public:
    ListNode* removeNthFromEnd(ListNode* head, int n) {
        //find the previous node of nth node from end and then remove it;

         ListNode* p=head;
         ListNode*temp=NULL;
         int i=0;

         while(p && i<n){
             p=p->next;
             i++;
         }

         while(p){
             p=p->next;
             if(temp==NULL) temp=head;
             else temp=temp->next;
         }

         //now temp is the node previous to nth node from end
         //remove temp->next

         ListNode* nthNode=NULL;

         if(temp==NULL) {
             //means n is equal to size of the linked list int
             nthNode=head;
             head=nthNode->next;
         }else{
             nthNode=temp->next;
             temp->next=nthNode->next;
         }
            
         delete nthNode;

         return head;
    }
};
```