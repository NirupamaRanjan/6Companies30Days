#  Minimum Time to Collect All Apples in a Tree &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/minimum-time-to-collect-all-apples-in-a-tree/description/)

```
Depth First Search, Tree
``` 
### Problem Statement 
Given an undirected tree consisting of n vertices numbered from 0 to n-1, which has some apples in their vertices. You spend 1 second to walk over one edge of the tree. Return the minimum time in seconds you have to spend to collect all apples in the tree, starting at vertex 0 and coming back to this vertex.

The edges of the undirected tree are given in the array edges, where edges[i] = [ai, bi] means that exists an edge connecting the vertices ai and bi. Additionally, there is a boolean array hasApple, where hasApple[i] = true means that vertex i has an apple; otherwise, it does not have any apple.

 
### Sample Input
```
n = 7, edges = [[0,1],[0,2],[1,4],[1,5],[2,3],[2,6]], hasApple = [false,false,true,false,true,true,false]
```
### Sample Output
```
8
```

### Solution
```cpp
class Solution {
public:
     vector<vector<int>>v;

     int dfs(int node,int parent,vector<bool>& hasApple){
           int timeTaken=0,timeTakenChild=0;
           for(auto child:v[node]){
               if(child==parent) continue;
               timeTakenChild=dfs(child,node,hasApple);
               if(timeTakenChild || hasApple[child]) timeTaken+=timeTakenChild+2;
           }

           return timeTaken;
     }

    int minTime(int n, vector<vector<int>>& edges, vector<bool>& hasApple) {
        v.resize(n);
        for(auto x: edges){
            v[x[0]].push_back(x[1]);
            v[x[1]].push_back(x[0]);
        }  
        int node=0,parent=-1;

        return dfs(node,parent,hasApple);
    }
};