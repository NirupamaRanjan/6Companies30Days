
# 4Sum &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/4sum/description//)

```
Array, Two pointers
``` 
### Problem Statement 
Given an array nums of n integers, return an array of all the unique quadruplets [nums[a], nums[b], nums[c], nums[d]] such that:

0 <= a, b, c, d < n
a, b, c, and d are distinct.
nums[a] + nums[b] + nums[c] + nums[d] == target
You may return the answer in any order.


### Sample Input
```
nums = [1,0,-1,0,-2,2], target = 0
```
### Sample Output
```
[[-2,-1,1,2],[-2,0,0,2],[-1,0,0,1]]
```

### Solution
```cpp
class Solution {  
public:
   class Solution {
public:
    vector<vector<int>> fourSum(vector<int>& nums, int target) {
        int n=nums.size();
        sort(nums.begin(),nums.end());
        vector<vector<int>>ans;
        if(n<4) return ans;

        for(int i=0;i<n-3;i++){
            //prevent duplicate
             if(i>0 && nums[i]==nums[i-1]) continue;
            //3sum ;
            for(int j=i+1;j<n-2;j++){
                //prevent duplicate
                 if(j>i+1 && nums[j]==nums[j-1]) continue;
                 
                long long t=nums[i]+nums[j];
                long long t2=target-t;
                 // 2sum ;
                int s=j+1;
                int e=n-1;

                while(s<e){
                   
                    long long sum=nums[s]+nums[e];
                    if(sum==t2){
                        ans.push_back({nums[i],nums[j],nums[s],nums[e]});
                        int temp1=nums[s];
                        int temp2=nums[e];
                        //prevent duplicate
                        while(s<n && nums[s]==temp1) s++;
                        while(e>=0 && nums[e]== temp2) e--;
                    }else if(sum>t2) e--;
                    else s++;
                } 
                 
            }
        }
        return ans;
    }
};
```