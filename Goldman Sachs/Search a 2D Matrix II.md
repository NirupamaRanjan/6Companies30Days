
# Search a 2D Matrix II &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/search-a-2d-matrix-ii/)

```
Matrix, Greedy
``` 
### Problem Statement 
Write an efficient algorithm that searches for a value target in an m x n integer matrix matrix. This matrix has the following properties:

Integers in each row are sorted in ascending from left to right.
Integers in each column are sorted in ascending from top to bottom.
### Sample Input
```
matrix = [[1,4,7,11,15],[2,5,8,12,19],[3,6,9,16,22],[10,13,14,17,24],[18,21,23,26,30]], target = 5
```
### Sample Output
```
true

```

### Solution
```cpp
class Solution {
public:
    bool searchMatrix(vector<vector<int>>& matrix, int target) {
        int row=0;
        int m=matrix.size();
        int n=matrix[0].size();
        //O(mlogn) solution use binary_search();
        
        //staircase search
        
        int i=0,j=n-1;
        
        while(i<m && j>=0){
            if(matrix[i][j]==target) return true;
            
            if(matrix[i][j]<target) i++;
            else j--;
        }
        
        
        return false;
    }
};
```