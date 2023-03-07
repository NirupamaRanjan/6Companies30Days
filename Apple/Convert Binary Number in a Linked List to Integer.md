
# Convert Binary Number in a Linked List to Integer &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/convert-binary-number-in-a-linked-list-to-integer/)

```
Linked List , Bit Manipulation
``` 
### Problem Statement 
Given head which is a reference node to a singly-linked list. The value of each node in the linked list is either 0 or 1. The linked list holds the binary representation of a number.

Return the decimal value of the number in the linked list.

The most significant bit is at the head of the linked list.

 
### Sample Input
```
head = [1,0,1]
```
### Sample Output
```
5
```

### Solution
```cpp
class Solution {
public:
    int getDecimalValue(ListNode* head) {
        int ans=0;

        while(head){
            int num=head->val;
            ans=(ans<<1) | num;
            head=head->next;
        }

        return ans;
    }
};