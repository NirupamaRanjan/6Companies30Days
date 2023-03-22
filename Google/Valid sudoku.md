
# Valid Sudoku &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/valid-sudoku/description/)

```
Matrix, Backtracking
``` 
### Problem Statement 
Determine if a 9 x 9 Sudoku board is valid. Only the filled cells need to be validated according to the following rules:

Each row must contain the digits 1-9 without repetition.
Each column must contain the digits 1-9 without repetition.
Each of the nine 3 x 3 sub-boxes of the grid must contain the digits 1-9 without repetition.
Note:

A Sudoku board (partially filled) could be valid but is not necessarily solvable.
Only the filled cells need to be validated according to the mentioned rules.
 

### Sample Input
```
board = 
[["5","3",".",".","7",".",".",".","."]
,["6",".",".","1","9","5",".",".","."]
,[".","9","8",".",".",".",".","6","."]
,["8",".",".",".","6",".",".",".","3"]
,["4",".",".","8",".","3",".",".","1"]
,["7",".",".",".","2",".",".",".","6"]
,[".","6",".",".",".",".","2","8","."]
,[".",".",".","4","1","9",".",".","5"]
,[".",".",".",".","8",".",".","7","9"]]
```
### Sample Output
```
true
```

### Solution
```cpp
class Solution {
public:
    
    
    bool isValid(int i,int j,int m,int n,char num,vector<vector<char>>& board){
          
        for(int row=i+1;row<m;row++)  if(board[row][j]==num)  return false;
        for(int col=j+1;col<n;col++)  if(board[i][col]==num)  return false;
        
        
        int sx=3*(i/3);
        int sy=3*(j/3);
        
        for(int row=sx;row<=sx+2;row++){
            for(int col=sy;col<=sy+2;col++){
                
                if(row==i && col==j) continue;
                
                if(board[row][col]==num) {
                    return false;
                }
                
            }
        }
        
        return true;
        
    }
    
    bool solve(vector<vector<char>>& board){
        
         int m=board.size();
         int n=board[0].size();
        
        for(int i=0;i<m;i++){
        for(int j=0;j<n;j++){
            if(board[i][j]!='.'){
                if(!isValid(i,j,m,n,board[i][j],board)){
                   return false;
                }
              }
            }
            
        }
        
        return true;
    }
    
    
    
    bool isValidSudoku(vector<vector<char>>& board) {
         
        return solve(board);
        
    }
};
```