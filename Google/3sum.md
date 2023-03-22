
# 3Sum &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/3sum/description/)

```
Array, Binary Search,Sorting
``` 
### Problem Statement 
Given an integer array nums, return all the triplets [nums[i], nums[j], nums[k]] such that i != j, i != k, and j != k, and nums[i] + nums[j] + nums[k] == 0.

Notice that the solution set must not contain duplicate triplets.

### Sample Input
```
nums = [-1,0,1,2,-1,-4]
```
### Sample Output
```
[[-1,-1,2],[-1,0,1]]
```

### Solution
```cpp
class Solution {
public:
    vector<vector<int>> threeSum(vector<int>& nums) {
        vector<vector<int>>ans;
        sort(nums.begin(),nums.end());
        set<vector<int>>s;

        for(int i=0;i<nums.size()-2;i++){
            int target=-(nums[i]);
            int j=i+1,k=nums.size()-1;

            while(j<k){
                int sum=nums[j]+nums[k];
                if(sum==target){
                    s.insert({nums[i],nums[j],nums[k]});
                    j++;
                    k--;
                }
                else if(sum<target) j++;
                else k--;
            }
        }

        for(auto x:s){
            ans.push_back(x);
        }

        return ans;
    }
};
```