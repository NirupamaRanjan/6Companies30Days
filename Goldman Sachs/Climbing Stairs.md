
# Climbing Stairs &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/climbing-stairs/description/)

```
Dynamic Programming
``` 
### Problem Statement 
You are climbing a staircase. It takes n steps to reach the top.

Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?
 

### Sample Input
```
n = 2
```
### Sample Output
```
2
```

### Solution
```cpp
class Solution {
public:
    int climbStairs(int n) {
        int dp[n+1];
        
        for(int i=0;i<=n;i++) dp[i]=0;
        
       dp[0]=1,dp[1]=1;
        
        for(int i=2;i<=n;i++){
            dp[i]=dp[i-1]+dp[i-2];
        }
        
       return dp[n]; 
    }
};
```