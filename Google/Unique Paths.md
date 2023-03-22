
# Unique Paths &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/unique-paths/description/)

```
Matrix, Dynamic Programming
``` 
### Problem Statement 
There is a robot on an m x n grid. The robot is initially located at the top-left corner (i.e., grid[0][0]). The robot tries to move to the bottom-right corner (i.e., grid[m - 1][n - 1]). The robot can only move either down or right at any point in time.

Given the two integers m and n, return the number of possible unique paths that the robot can take to reach the bottom-right corner.

The test cases are generated so that the answer will be less than or equal to 2 * 109.

### Sample Input
```
m = 3, n = 7
```
### Sample Output
```
28
```

### Solution
```cpp
class Solution {
public:
    
    vector<vector<int>>dp;

    int uniquePaths(int m, int n) {
        //initialize with 1 because we need to move 1 step from each block
        dp.resize(m+1,vector<int>(n+1,1));
        dp[m][n]=0;
        dp[m-1][n-1]=1;

        for(int i=m-2;i>=0;i--){
            for(int j=n-2;j>=0;j--){
                dp[i][j]=dp[i+1][j]+dp[i][j+1];
            }
        }
       return dp[0][0];
    }
};
```