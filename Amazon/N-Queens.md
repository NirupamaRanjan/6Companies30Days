
# N-Queens &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/n-queens/)

```
Backtracking
``` 
### Problem Statement 

The n-queens puzzle is the problem of placing n queens on an n x n chessboard such that no two queens attack each other.

Given an integer n, return all distinct solutions to the n-queens puzzle. You may return the answer in any order.

Each solution contains a distinct board configuration of the n-queens' placement, where 'Q' and '.' both indicate a queen and an empty space, respectively.

### Sample Input
```
n = 4
```
### Sample Output
```
[[".Q..","...Q","Q...","..Q."],["..Q.","Q...","...Q",".Q.."]]
```

### Solution
```cpp
class Solution {
public:
    
    bool canPlace(int i,int j, vector<string>m,int n){
      //upper rows
        for(int k=0;k<i;k++){
            if(m[k][j]=='Q') return false;
        }
        
        // left diagonal
        
        int x=i;
        int y=j;
        while(x>0 && y>0){
            if(m[x-1][y-1]=='Q') return false;
            x--;
            y--;
        }
        
        // right diagonal
        x=i;
        y=j;
        while(x>0 && y<n ){
             if(m[x-1][y+1]=='Q') return false;
             x--;
             y++;
        }
        
        return true;
    }
    
    
    bool placeQueen(int row,vector<vector<string>>&ans,vector<string>&a,int n){
        if(row==n){
            ans.push_back(a);
            return false;
        }
        
        for(int col=0;col<n;col++){
            if(canPlace(row,col,a,n)){
                a[row][col]='Q';
                bool x=placeQueen(row+1,ans,a,n);
                if(x) return true;
                a[row][col]='.';
            }
        }
       return false;
    }
    
    
    vector<vector<string>> solveNQueens(int n) {
    
        vector<string>a(n);
        
        for(int i=0;i<n;i++){
            string s="";
            for(int j=0;j<n;j++){
              s+=".";
            }
            a[i]=s;
        }
        // for(int i=0;i<n;i++){
        //    cout<<a[i]<<" ";
        // }
        
        int row=0;       
        vector<vector<string>>ans;
        placeQueen(row,ans,a,n);
        return ans;
        
    }
};