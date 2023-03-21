
# First Missing Positive &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/first-missing-positive/description/)

```
Array
``` 
### Problem Statement 
Given an unsorted integer array nums, return the smallest missing positive integer.

You must implement an algorithm that runs in O(n) time and uses constant extra space.

### Sample Input
```
nums = [1,2,0]
```
### Sample Output
```
3
```

### Solution
```cpp
class Solution {
public:
    int firstMissingPositive(vector<int>& nums) {
        int n=nums.size();

        for(int i=0;i<n;i++){
            while(nums[i]>0 && nums[i]<=n && nums[nums[i]-1]!=nums[i]){
               swap(nums[nums[i]-1],nums[i]);
            }
        }


        for(int i=0;i<n;i++){
            if(nums[i]!=i+1) return i+1;
        }

        return n+1;
    }
};
```