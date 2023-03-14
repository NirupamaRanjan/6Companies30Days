
# Minimum Size Subarray Sum &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/minimum-size-subarray-sum/description/)

```
Array, Sliding Window
``` 
### Problem Statement 
Given an array of positive integers nums and a positive integer target, return the minimal length of a 
subarray
 whose sum is greater than or equal to target. If there is no such subarray, return 0 instead.
### Sample Input
```
target = 7, nums = [2,3,1,2,4,3]
```
### Sample Output
```
2
```

### Solution
```cpp
class Solution {
public:
    int minSubArrayLen(int target, vector<int>& nums) {
       int n=nums.size();
      int i=0,j=0;
        int s=0;
        
        int ans=INT_MAX;
        while(j<n){
            s+=nums[j];
            
            if(s<target) j++;
            else if(s==target) {
                ans=min(ans,j-i+1);
                j++;
            }else if(s>target){
                while(s>target){
                    ans=min(ans,j-i+1);
                    s-=nums[i];
                    i++;
                }
                
                if(s==target) ans=min(ans,j-i+1);
                j++;
            }
        }
        
        return ans==INT_MAX?0:ans; 
    }
};
```