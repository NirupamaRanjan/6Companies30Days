
# Search in Rotated Sorted Array &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/search-in-rotated-sorted-array/description/)

```
Array, Binary Search
``` 
### Problem Statement 
There is an integer array nums sorted in ascending order (with distinct values).

Prior to being passed to your function, nums is possibly rotated at an unknown pivot index k (1 <= k < nums.length) such that the resulting array is [nums[k], nums[k+1], ..., nums[n-1], nums[0], nums[1], ..., nums[k-1]] (0-indexed). For example, [0,1,2,4,5,6,7] might be rotated at pivot index 3 and become [4,5,6,7,0,1,2].

Given the array nums after the possible rotation and an integer target, return the index of target if it is in nums, or -1 if it is not in nums.

You must write an algorithm with O(log n) runtime complexity.

### Sample Input
```
nums = [4,5,6,7,0,1,2], target = 0
```
### Sample Output
```
4
```

### Solution
```cpp
class Solution {
public:
    int search(vector<int>& nums, int target) {
        int s=0,e=nums.size()-1;
        while(s<=e){
            int mid=s+(e-s)/2;
            if(nums[mid]==target) return mid;
            else if(nums[mid]>=nums[s]){
                  //means we are in first half of sorted array;
                  if(nums[mid]>target && target>=nums[s]){
                      //additional check for target>=nums[s] is required to check if target also lies in first half
                    e=mid-1;
                  }else{
                     s=mid+1;  
                  }
            }else{
                if(nums[mid]<target && target<=nums[e]){
                    s=mid+1;
                }else{
                    e=mid-1;
                }
            }
        }
        return -1;
    }
};