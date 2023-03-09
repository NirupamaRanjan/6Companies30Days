# Linked List Cycle II &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/linked-list-cycle-ii/)

```
Linked List
``` 
### Problem Statement 
Given the head of a linked list, return the node where the cycle begins. If there is no cycle, return null.

There is a cycle in a linked list if there is some node in the list that can be reached again by continuously following the next pointer. Internally, pos is used to denote the index of the node that tail's next pointer is connected to (0-indexed). It is -1 if there is no cycle. Note that pos is not passed as a parameter.

Do not modify the linked list.


### Sample Input
```
head = [3,2,0,-4], pos = 1
```
### Sample Output
```
tail connects to node index 1
```

### Solution
```cpp
class Solution {
public:
    ListNode *detectCycle(ListNode *head) {
          if(head==NULL || head->next==NULL) return NULL;

          ListNode* slow=head;
          ListNode* fast=head;

          while(fast && fast->next){
              slow=slow->next;
              fast=fast->next->next;
              if(slow==fast){
                  break;
              } 
          }

         if(slow!=fast) return NULL;

          cout<<fast->val<<" "<<slow->val<<endl;

          slow=head;
          while(slow!=fast){
              slow=slow->next;
              fast=fast->next;
          }


          return fast;
          
    }
};