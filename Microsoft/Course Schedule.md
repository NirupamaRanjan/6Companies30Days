
# Course Schedule &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/course-schedule/description/)

```
Graph, Topological sort
``` 
### Problem Statement 
There are a total of numCourses courses you have to take, labeled from 0 to numCourses - 1. You are given an array prerequisites where prerequisites[i] = [ai, bi] indicates that you must take course bi first if you want to take course ai.

For example, the pair [0, 1], indicates that to take course 0 you have to first take course 1.
Return true if you can finish all courses. Otherwise, return false.
### Sample Input
```
numCourses = 2, prerequisites = [[1,0]]
```
### Sample Output
```
true
```

### Solution
```cpp
class Solution {
public:
    bool canFinish(int numCourses, vector<vector<int>>& pre) {
        
        vector<vector<int>>graph(numCourses);
        
        vector<int>inorder(numCourses,0);
        
        for(int i=0;i<pre.size();i++){ 
          inorder[pre[i][0]]++;  
          graph[pre[i][1]].push_back(pre[i][0]);
        }
        
        vector<int>courses;
        
        queue<int>q;
        
        for(int i=0;i<inorder.size();i++){
            if(inorder[i]==0) q.push(i);
        }
        
        while(!q.empty()){
            int i=q.front();
            courses.push_back(i);
            q.pop();
            for(auto x:graph[i]){
                inorder[x]--;
                if(inorder[x]==0) {
                    q.push(x);
                }
            }
            
            
        }
        return (courses.size()==numCourses);
        
        
    }
};
```