
# Minimum Path Sum &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/minimum-path-sum/description/)

```
Matrix, Dynamic Programming
``` 
### Problem Statement 
Given a m x n grid filled with non-negative numbers, find a path from top left to bottom right, which minimizes the sum of all numbers along its path.

Note: You can only move either down or right at any point in time.

### Sample Input
```
grid = [[1,3,1],[1,5,1],[4,2,1]]
```
### Sample Output
```
7
```

### Solution
```cpp
class Solution {
public:

    int minPathSum(vector<vector<int>>& grid) {
     int m=grid.size(); 
     int n=grid[0].size();
    
        for(int i=0;i<m;i++){
           for(int j=0;j<n;j++){
              if(i==0 && j==0)  continue;
              else if (i==0) grid[i][j]+=grid[i][j-1];
              else if(j==0) grid[i][j]+=grid[i-1][j];
              else grid[i][j]+=min(grid[i-1][j],grid[i][j-1]);
           }
        }
     
        return grid[m-1][n-1];
        
    }
};
```