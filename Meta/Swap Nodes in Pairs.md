
# Swap Nodes in Pairs &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/swap-nodes-in-pairs/description/)

```
Linked List, Recursion
``` 
### Problem Statement 
Given a linked list, swap every two adjacent nodes and return its head. You must solve the problem without modifying the values in the list's nodes (i.e., only nodes themselves may be changed.)
 
### Sample Input
```
head = [1,2,3,4]
```
### Sample Output
```
[2,1,4,3]
```

### Solution
```cpp
class Solution {
public:
    ListNode* swapPairs(ListNode* head) {
     if(head==NULL || head->next==NULL) return head;

        //swap nodes here
       ListNode* temp=head->next;
       head->next=swapPairs(head->next->next);
       temp->next=head;

      return  temp;
    }
};
```