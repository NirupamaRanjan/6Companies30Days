
# Longest Increasing Subsequence &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/longest-increasing-subsequence/)

```
Dynamic Programming
``` 
### Problem Statement 
Given an integer array nums, return the length of the longest strictly increasing 
subsequence.

### Sample Input
```
nums = [10,9,2,5,3,7,101,18]
```
### Sample Output
```
 4
```

### Solution
```cpp
class Solution {
public:
    int lengthOfLIS(vector<int>& nums) {
        int n=nums.size();
        vector<int>dp(n+1,1);
        
        for(int i=1;i<n;i++){
          for(int j=i-1;j>=0;j--){
              if(nums[i]>nums[j]){
                  dp[i]=max(dp[i],dp[j]+1);
              }
          }
        }
        
        return *max_element(dp.begin(),dp.end());
    }
};