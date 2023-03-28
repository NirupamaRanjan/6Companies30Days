
# Coin Change &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/remove-duplicates-from-sorted-array-ii/description/)

```
Array, Two Pointers
``` 
### Problem Statement 
Given an integer array nums sorted in non-decreasing order, remove some duplicates in-place such that each unique element appears at most twice. The relative order of the elements should be kept the same.

Since it is impossible to change the length of the array in some languages, you must instead have the result be placed in the first part of the array nums. More formally, if there are k elements after removing the duplicates, then the first k elements of nums should hold the final result. It does not matter what you leave beyond the first k elements.

Return k after placing the final result in the first k slots of nums.

Do not allocate extra space for another array. You must do this by modifying the input array in-place with O(1) extra memory.

### Sample Input
```
nums = [1,1,1,2,2,3]
```
### Sample Output
```
5, nums = [1,1,2,2,3,_]
```

### Solution
```cpp
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        int n=nums.size();
        int i=0,j=0;
        if(n==0 || n==1) return n;
        
        if(nums[0]==nums[1]) i++;

        while(j<n){
            if(nums[i]!=nums[j]){
                i++;
                nums[i]=nums[j];
                if(j<n-1 && nums[j]==nums[j+1]){
                    i++;
                    j++;
                    nums[i]=nums[j];
                }

            }else{
                j++;
            }
        }

        return i+1;
    }
};
```