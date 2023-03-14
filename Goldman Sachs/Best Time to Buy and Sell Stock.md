
# Best Time to Buy and Sell Stock &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)

```
Array, Dynamic Programming
``` 
### Problem Statement 
You are given an array prices where prices[i] is the price of a given stock on the ith day.

You want to maximize your profit by choosing a single day to buy one stock and choosing a different day in the future to sell that stock.

Return the maximum profit you can achieve from this transaction. If you cannot achieve any profit, return 0.


### Sample Input
```
prices = [7,1,5,3,6,4]
```
### Sample Output
```
5
```

### Solution
```cpp
class Solution {
public:
    int maxProfit(vector<int>& prices) {
       int n=prices.size();
        int maxTillNow=prices[n-1];
        int profit=0;
        
        for(int i=n-2;i>=0;i--){
            maxTillNow=max(maxTillNow,prices[i]);
            profit=max(profit,maxTillNow-prices[i]); 
        }
        
        return profit;
    }
};
```