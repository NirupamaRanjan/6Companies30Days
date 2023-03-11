
# Spiral Matrix &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/spiral-matrix/description/)

```
Matrix
``` 
### Problem Statement 
Given an m x n matrix, return all elements of the matrix in spiral order.
### Sample Input
```
matrix = [[1,2,3],[4,5,6],[7,8,9]]
```
### Sample Output
```
[1,2,3,6,9,8,7,4,5]
```

### Solution
```cpp
class Solution {
public:
    vector<int> spiralOrder(vector<vector<int>>& matrix) {
        vector<int>ans;
        
        int m=matrix.size();
        int n=matrix[0].size();
        
        int si=0,sj=0,ei=m-1,ej=n-1;
        
        
        
        while(si<=ei && sj<=ej){
            

        for(int j=sj;j<=ej;j++){
          ans.push_back(matrix[si][j]);
        }
        si++;
        
            
        
        for(int i=si;i<=ei;i++){
            ans.push_back(matrix[i][ej]);
        }
        ej--;
        
            
    
       if(ei>=si){
        for(int j=ej;j>=sj;j--){
            ans.push_back(matrix[ei][j]);
        }
        ei--;
       }
            
        if(ej>=sj){
        for(int i=ei;i>=si;i--){
            ans.push_back(matrix[i][sj]);
        }
        sj++;
        }    
            
        }
        
        
        return ans;
    }
};
```