
# Pacific Atlantic Water Flow &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/pacific-atlantic-water-flow/description/)

```
Matrix, Dfs
``` 
### Problem Statement 
There is an m x n rectangular island that borders both the Pacific Ocean and Atlantic Ocean. The Pacific Ocean touches the island's left and top edges, and the Atlantic Ocean touches the island's right and bottom edges.

The island is partitioned into a grid of square cells. You are given an m x n integer matrix heights where heights[r][c] represents the height above sea level of the cell at coordinate (r, c).

The island receives a lot of rain, and the rain water can flow to neighboring cells directly north, south, east, and west if the neighboring cell's height is less than or equal to the current cell's height. Water can flow from any cell adjacent to an ocean into the ocean.

Return a 2D list of grid coordinates result where result[i] = [ri, ci] denotes that rain water can flow from cell (ri, ci) to both the Pacific and Atlantic oceans.


### Sample Input
```
heights = [[1,2,2,3,5],[3,2,3,4,4],[2,4,5,3,1],[6,7,1,4,5],[5,1,1,2,4]]
```
### Sample Output
```
[[0,4],[1,3],[1,4],[2,2],[3,0],[3,1],[4,0]]
```

### Solution
```cpp
class Solution {
public:
   vector<vector<int>>ans;
   vector<vector<bool>>pacific;
   vector<vector<bool>>atlantic;

   vector<int>dx={-1,1,0,0};
   vector<int>dy={0,0,-1,1};

   void solve(vector<vector<int>>& h,vector<vector<bool>>&mat,int i,int j,int m,int n){
        //it means it is already viisted;
        if(mat[i][j]) return ;
        mat[i][j]=true;

        if(pacific[i][j] && atlantic[i][j]) ans.push_back({i,j});

        for(int k=0;k<4;k++){
             int ni=i+dx[k],nj=j+dy[k];
             if(ni>=0 && ni<m && nj>=0 && nj<n && h[ni][nj]>=h[i][j]) solve(h,mat,ni,nj,m,n);
        }
   }
      
    vector<vector<int>> pacificAtlantic(vector<vector<int>>& heights) {
       int m=heights.size();
       int n=heights[0].size();

       pacific.resize(m,vector<bool>(n,false));
       atlantic.resize(m,vector<bool>(n,false));

       //thinking in reverse manner i.e, from rivers to grid

      for(int j=0;j<n;j++) {
          solve(heights,pacific,0,j,m,n);
          solve(heights,atlantic,m-1,j,m,n);
      }

      for(int i=0;i<m;i++) {
          solve(heights,pacific,i,0,m,n);
          solve(heights,atlantic,i,n-1,m,n);
      }
       return ans;  
    }
};
```