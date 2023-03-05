# Kth Largest Sum in a Binary Tree &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/kth-largest-sum-in-a-binary-tree/)

```
Binary Tree, Breadth First Search
``` 
### Problem Statement 

You are given the root of a binary tree and a positive integer k.

The level sum in the tree is the sum of the values of the nodes that are on the same level.

Return the kth largest level sum in the tree (not necessarily distinct). If there are fewer than k levels in the tree, return -1.

Note that two nodes are on the same level if they have the same distance from the root.

### Sample Input
```
root = [5,8,9,2,1,3,7,4,6], k = 2
```
### Sample Output
```
13
```

### Solution
```cpp
class Solution {
public:
    
    static bool myComp(long long a,long long b){
        return a>b;
    }
    
    long long kthLargestLevelSum(TreeNode* root, int k) {
        vector<long long>v;
        
        queue<TreeNode*>q;
        q.push(root);
        
        while(!q.empty()){
            long long sum=0;
            long long l=q.size();
            while(l){
                 TreeNode* t=q.front();
                 q.pop();
                 sum+=t->val;
                if(t->left) q.push(t->left);
                if(t->right) q.push(t->right);
                l--;
            }  
            v.push_back(sum);
        }
        
        if(v.size()<k) return -1;
        sort(v.begin(),v.end(),myComp);
        return v[k-1];
        
    }
};