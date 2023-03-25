
# Search in Rotated Sorted Array II &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/search-in-rotated-sorted-array-ii/description/)

```
Array, Binary Search
``` 
### Problem Statement 
There is an integer array nums sorted in non-decreasing order (not necessarily with distinct values).

Before being passed to your function, nums is rotated at an unknown pivot index k (0 <= k < nums.length) such that the resulting array is [nums[k], nums[k+1], ..., nums[n-1], nums[0], nums[1], ..., nums[k-1]] (0-indexed). For example, [0,1,2,4,4,4,5,6,6,7] might be rotated at pivot index 5 and become [4,5,6,6,7,0,1,2,4,4].

Given the array nums after the rotation and an integer target, return true if target is in nums, or false if it is not in nums.

You must decrease the overall operation steps as much as possible.

 
 
### Sample Input
```
nums = [2,5,6,0,0,1,2], target = 3
```
### Sample Output
```
false
```

### Solution
```cpp
class Solution {
public:
    bool search(vector<int>& nums, int target) {
        int n=nums.size();
        int s=0,e=n-1;

        while(s<=e){
            int mid=s+(e-s)/2;

            if(nums[mid]==target) return true;
            
            //for duplicate elements
            if((nums[s]==nums[mid]) &&  (nums[e]==nums[mid])){
                s++;
                e--;
            }

            else if(nums[mid]>=nums[s]){
                 if(nums[mid]>target && nums[s]<=target) e=mid-1;
                 else s=mid+1;
            }else{
                 if(nums[mid]<target && nums[e]>=target) s=mid+1;
                 else e= mid-1;
            }
        }

        return false;
    }
};
```