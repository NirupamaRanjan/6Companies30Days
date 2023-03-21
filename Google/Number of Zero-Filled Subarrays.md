
# Number of Zero-Filled Subarrays &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/number-of-zero-filled-subarrays/description/)

```
Array, Math
``` 
### Problem Statement 
Given an integer array nums, return the number of subarrays filled with 0.

A subarray is a contiguous non-empty sequence of elements within an array.

### Sample Input
```
nums = [0,0,0,2,0,0]
```
### Sample Output
```
9
```

### Solution
```cpp
class Solution {
public:
    long long zeroFilledSubarray(vector<int>& nums) {
        int n=nums.size();
        long long ans=0;
        long long l=0;
        int i=0;
        
       //Just doing 1+2+3+4+....l in ans. As the no of subarray for l length will be sum from 1 to l. And when nums[i]!=0 length is back to 0 
        while(i<n){
           if(nums[i++]==0) l++;
           else l=0;

           ans+=l;
        }

        return ans;
    }
};
```