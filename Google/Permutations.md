
# Permutations &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/permutations/description/)

```
Array, Backtracking
``` 
### Problem Statement 
Given an array nums of distinct integers, return all the possible permutations. You can return the answer in any order.

### Sample Input
```
nums = [1,2,3]
```
### Sample Output
```
[[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]
```

### Solution
```cpp
class Solution {
public:
    vector<vector<int>>ans;
    
    void solution(vector<int>& nums,int i){
        if(i==nums.size()){
            ans.push_back(nums);
            return;
        }     
        for(int j=i;j<nums.size();j++){
            swap(nums[i],nums[j]);
            solution(nums,i+1);
            swap(nums[i],nums[j]);
        }
    }
    
    vector<vector<int>> permute(vector<int>& nums) {
        solution(nums,0);
        return ans;
    }
};
```