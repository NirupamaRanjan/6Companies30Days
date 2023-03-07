# Kth Largest Sum in a Binary Tree &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/add-two-numbers/description/)

```
Linked List
``` 
### Problem Statement 

You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.
### Sample Input
```
l1 = [2,4,3], l2 = [5,6,4]
```
### Sample Output
```
[7,0,8]
```

### Solution
```cpp
class Solution {
public:
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        ListNode* ans=NULL;
        ListNode* temp=NULL;
        int sum=0;

        while(l1 || l2 || sum){
            if(l1){
                sum+=l1->val;
                l1=l1->next;
            }

            if(l2){
                sum+=l2->val;
                l2=l2->next;
            }

            if(ans==NULL){
                ans=new ListNode(sum%10);
                temp=ans;
            }else{
                temp->next=new ListNode(sum%10);
                temp=temp->next;
            }
            sum=sum/10;
        }
         return ans;
    }

   
};