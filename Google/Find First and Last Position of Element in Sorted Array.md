
# Find First and Last Position of Element in Sorted Array &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/description/)

```
Array, Binary Search
``` 
### Problem Statement 
Given an array of integers nums sorted in non-decreasing order, find the starting and ending position of a given target value.

If target is not found in the array, return [-1, -1].

You must write an algorithm with O(log n) runtime complexity.


### Sample Input
```
nums = [5,7,7,8,8,10], target = 8
```
### Sample Output
```
[3,4]
```

### Solution
```cpp
class Solution {
public:
    vector<int> searchRange(vector<int>& nums, int target) {
        int n=nums.size();
        int s=0,e=n-1;
        vector<int>ans;
        
        int se=-1 ,ee=-1;
        
        while(s<=e){
            int mid=(s+e)/2;
            if(nums[mid]==target) { 
              se=mid;
              e--;
            }
            
            else if(nums[mid]>target) e--;
            else s++;
        }
        
         s=0,e=n-1;
        
         while(s<=e){
            int mid=(s+e)/2;
            if(nums[mid]==target) {
                s++;
                ee=mid;
            }
            
            else if(nums[mid]>target) e--;
            else s++;
        }
        
         ans.push_back(se);
         ans.push_back(ee);
        
        return ans;
         
    }
};
```