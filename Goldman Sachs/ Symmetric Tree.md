
# Symmetric Tree &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/symmetric-tree/description/)

```
Binary Tree
``` 
### Problem Statement 
Given the root of a binary tree, check whether it is a mirror of itself (i.e., symmetric around its center).

### Sample Input
```
root = [1,2,2,3,4,4,3]
```
### Sample Output
```
true
```

### Solution
```cpp
class Solution {
public:

    bool solve(TreeNode* leftNode,TreeNode* rightNode){
        if(leftNode==NULL && rightNode==NULL) return true;
        if(leftNode==NULL || rightNode==NULL) return false;

        if(leftNode->val != rightNode->val) return false;

        return solve(leftNode->left,rightNode->right) && solve(leftNode->right,rightNode->left) ;
    
    }



    bool isSymmetric(TreeNode* root) {
       if(root==NULL) return true;
       return solve(root->left,root->right);
    }
};
```