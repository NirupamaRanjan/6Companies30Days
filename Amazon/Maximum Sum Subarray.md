# Maximum Sum Subarray[![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/maximum-subarray/)

```
Array, Divide and Conquer, Dynamic Programming
``` 
### Problem Statement 

Given an integer array nums, find the 
subarray
 with the largest sum, and return its sum.

### Sample Input
```
nums = [-2,1,-3,4,-1,2,1,-5,4]
```
### Sample Output
```
6
```

### Solution
```cpp
class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        int max_sum=INT_MIN,current_sum=0, max_element=INT_MIN;
        
        for(int i=0;i<nums.size();i++){
            current_sum+=nums[i];
            if(current_sum<0) current_sum=0;
            max_sum=max(max_sum,current_sum);
            max_element=max(max_element,nums[i]);
        }
        
        if(max_sum==0) return max_element;
        return max_sum;
        
        
    }
};
`