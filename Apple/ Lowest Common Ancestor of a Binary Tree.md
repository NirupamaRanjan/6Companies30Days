
# Lowest Common Ancestor of a Binary Tree &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/)

```
Binary Tree
``` 
### Problem Statement 
Given a binary tree, find the lowest common ancestor (LCA) of two given nodes in the tree.

According to the definition of LCA on Wikipedia: “The lowest common ancestor is defined between two nodes p and q as the lowest node in T that has both p and q as descendants (where we allow a node to be a descendant of itself).”


### Sample Input
```
root = [3,5,1,6,2,0,8,null,null,7,4], p = 5, q = 1
```
### Sample Output
```
 3
```

### Solution
```cpp
class Solution {
public:
    TreeNode* lowestCommonAncestor(TreeNode* root, TreeNode* p, TreeNode* q) {
        if(root==NULL) return NULL;
        
        if(root==p || root==q) return root;
        
        TreeNode*l=lowestCommonAncestor(root->left,p,q);
        TreeNode*r=lowestCommonAncestor(root->right,p,q);
        
        if(l && r) return root;
        if(l) return l;
        if(r) return r;
        return NULL;
    }
};
```