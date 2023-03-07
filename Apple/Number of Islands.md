# Number of Islands &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/number-of-islands/description/)

```
Matrix, Depth First Search
``` 
### Problem Statement 

Given an m x n 2D binary grid grid which represents a map of '1's (land) and '0's (water), return the number of islands.

An island is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. You may assume all four edges of the grid are all surrounded by water.

### Sample Input
```
grid = [
  ["1","1","1","1","0"],
  ["1","1","0","1","0"],
  ["1","1","0","0","0"],
  ["0","0","0","0","0"]
]
```
### Sample Output
```
1
```

### Solution
```cpp
class Solution {
public:
   
      
    void dfs(vector<vector<char>>& grid,vector<vector<bool>>&visited,int i ,int j ,int n,int m){
        
        int dx[]={-1,0,1,0};
        int dy[]={0,-1,0,1};
       
        if(i<0 || j<0 || i==n || j==m) return;
        if(grid[i][j]=='0' || visited[i][j]) return ;
        
        visited[i][j]=true;
        
        for(int k=0;k<4;k++){
            dfs(grid,visited,i+dx[k],j+dy[k],n,m);
        }
       return;        
    }
    
    int numIslands(vector<vector<char>>& grid) {
        
        int ans=0;
        int n=grid.size();
        int m=grid[0].size();
        
        vector<vector<bool>>visited(n,vector<bool>(m,false));
        for(int i=0;i<n;i++){
            for(int j=0;j<m;j++){
                if(grid[i][j]=='1' && !visited[i][j]){
                    dfs(grid,visited,i,j,n,m);
                    ans++;
                }
            }
        }
     return ans;   
    }
};