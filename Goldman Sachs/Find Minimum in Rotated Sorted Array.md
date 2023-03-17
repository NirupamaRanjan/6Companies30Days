
# Find Minimum in Rotated Sorted Array &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/description/)

```
Array, Binary Search
``` 
### Problem Statement 
Suppose an array of length n sorted in ascending order is rotated between 1 and n times. For example, the array nums = [0,1,2,4,5,6,7] might become:

[4,5,6,7,0,1,2] if it was rotated 4 times.
[0,1,2,4,5,6,7] if it was rotated 7 times.
Notice that rotating an array [a[0], a[1], a[2], ..., a[n-1]] 1 time results in the array [a[n-1], a[0], a[1], a[2], ..., a[n-2]].

Given the sorted rotated array nums of unique elements, return the minimum element of this array.

You must write an algorithm that runs in O(log n) time.

### Sample Input
```
nums = [3,4,5,1,2]
```
### Sample Output
```
1
```

### Solution
```cpp
class Solution {
public:
    int findMin(vector<int>& nums) {
        int n=nums.size();
        int s=0;
        int e=n-1;
        int ans=INT_MAX;

        while(s<=e){
            
            if(nums[s]<=nums[e]){
                //now we are in the 2nd sorted part
                ans=min(ans,nums[s]);
                return ans;
            }

            int mid=s+(e-s)/2;
            //keep track of minimum value
            ans=min(ans,nums[mid]);

            if(nums[s]<=nums[mid]){
                s=mid+1;
            }else{
                e=mid-1;
            }
        }

        return  ans;
    }
};
```