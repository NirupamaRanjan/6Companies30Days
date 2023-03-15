
# Check Completeness of a Binary Tree &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/check-completeness-of-a-binary-tree/)

```
Binary Tree, Breadth First search
``` 
### Problem Statement 
Given the root of a binary tree, determine if it is a complete binary tree.

In a complete binary tree, every level, except possibly the last, is completely filled, and all nodes in the last level are as far left as possible. It can have between 1 and 2h nodes inclusive at the last level h.
### Sample Input
```
root = [1,2,3,4,5,6]
```
### Sample Output
```
true
```

### Solution
```cpp
class Solution {
public:
    bool isCompleteTree(TreeNode* root) {
        queue<TreeNode*> q;
        q.push(root);
        bool firstNULL=false;

        while(!q.empty()){
                 TreeNode* parent=q.front();
                 q.pop();

                 if(parent==NULL){
                     firstNULL=true;
                 }else{
                     if(firstNULL) return false;
                     q.push(parent->left);
                     q.push(parent->right);
                 }
        }

        return true;
    }
};
```