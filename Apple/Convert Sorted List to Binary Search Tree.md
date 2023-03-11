# Convert Sorted List to Binary Search Tree &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/convert-sorted-list-to-binary-search-tree/description/)

```
Linked List, Binary Search Tree
``` 
### Problem Statement 
Given the head of a singly linked list where elements are sorted in ascending order, convert it to a 
height-balanced
 binary search tree.

### Sample Input
```
head = [-10,-3,0,5,9]
```
### Sample Output
```
[0,-3,9,-10,null,5]
```

### Solution
```cpp
class Solution {
public:

     ListNode* prevMid(ListNode*head){
         ListNode* slow=head;
         ListNode* fast=head->next->next;

         while(fast && fast->next){
             slow=slow->next;
             fast=fast->next->next;
         }
         return slow;
     }

    TreeNode* sortedListToBST(ListNode* head) {
        if(head==NULL) return NULL;
        if(head->next==NULL) return new TreeNode(head->val);
        //List Node previous to mid node
        ListNode* pMid=prevMid(head);
        TreeNode* root=new TreeNode(pMid->next->val);

        ListNode* right=pMid->next->next;
        pMid->next=NULL;
        root->left=sortedListToBST(head);
        root->right=sortedListToBST(right);
        return root;
    }
};