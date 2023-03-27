
# Coin Change &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/coin-change/)

```
Array, Dynamic Programming
``` 
### Problem Statement 
You are given an integer array coins representing coins of different denominations and an integer amount representing a total amount of money.

Return the fewest number of coins that you need to make up that amount. If that amount of money cannot be made up by any combination of the coins, return -1.

You may assume that you have an infinite number of each kind of coin.


### Sample Input
```
coins = [1,2,5], amount = 11
```
### Sample Output
```
3
```

### Solution
```cpp
class Solution {
public:
    int coinChange(vector<int>& coins, int amount) {
        int n=coins.size();
        
        vector<vector<int>>dp(n+1,vector<int>(amount+1,0));
        
        for(int j=1;j<=amount;j++) dp[0][j]=INT_MAX-1;
        
        for(int i=1;i<=n;i++){
            for(int j=1;j<=amount;j++){
                
                if(j-coins[i-1]>=0){
                    dp[i][j]=min(1+dp[i][j-coins[i-1]],dp[i-1][j]);
                }else{
                    dp[i][j]=dp[i-1][j];
                }
            }
        }
    
        
        return dp[n][amount]==INT_MAX-1?-1:dp[n][amount];
        
    }
};
```