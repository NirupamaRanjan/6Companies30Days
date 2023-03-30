
# Set Matrix Zeroes &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/set-matrix-zeroes/description/)

```
Matrix
``` 
### Problem Statement 
Given an m x n integer matrix matrix, if an element is 0, set its entire row and column to 0's.

You must do it in place.

### Sample Input
```
matrix = [[1,1,1],[1,0,1],[1,1,1]]
```
### Sample Output
```
[[1,0,1],[0,0,0],[1,0,1]]
```

### Solution
```cpp
class Solution {
public:
    
    void solve(int i,int j,int m,int n ,vector<vector<int>>& matrix,vector<vector<bool>>&visited){
        
        visited[i][j]=true;
        
         for(int y=0;y<n;y++){
             if(matrix[i][y]!=0){
                 matrix[i][y]=0;
                 visited[i][y]=true;
             }
            
         }

         for(int x=0;x<m;x++){
             if(!matrix[x][j]==0){
                 matrix[x][j]=0;
                 visited[x][j]=true;
             }
            
         }
        
    }
    
    void setZeroes(vector<vector<int>>& matrix) {
        int m=matrix.size();
        int n=matrix[0].size();
        
        vector<vector<bool>>visited(m,vector<bool>(n,false));
        
        for(int i=0;i<m;i++){
            for(int j=0;j<n;j++){
             if(matrix[i][j]==0 && visited[i][j]==false){
                 solve(i,j,m,n,matrix,visited);    
                }
            }
        }
    }
};
```