
# Next Permutation &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/next-permutation/)

```
Array, Two pointers
``` 
### Problem Statement 
A permutation of an array of integers is an arrangement of its members into a sequence or linear order.

For example, for arr = [1,2,3], the following are all the permutations of arr: [1,2,3], [1,3,2], [2, 1, 3], [2, 3, 1], [3,1,2], [3,2,1].
The next permutation of an array of integers is the next lexicographically greater permutation of its integer. More formally, if all the permutations of the array are sorted in one container according to their lexicographical order, then the next permutation of that array is the permutation that follows it in the sorted container. If such arrangement is not possible, the array must be rearranged as the lowest possible order (i.e., sorted in ascending order).

For example, the next permutation of arr = [1,2,3] is [1,3,2].
Similarly, the next permutation of arr = [2,3,1] is [3,1,2].
While the next permutation of arr = [3,2,1] is [1,2,3] because [3,2,1] does not have a lexicographical larger rearrangement.
Given an array of integers nums, find the next permutation of nums.

The replacement must be in place and use only constant extra memory.

### Sample Input
```
[1,2,3]
```
### Sample Output
```
[1,3,2]
```

### Solution
```cpp
class Solution {
public:
    void nextPermutation(vector<int>& nums) {
       int n=nums.size();
       if(n==0 || n==1) return ;

       int firstBreakPoint=-1;
      for(int i=n-2;i>=0;i--){
          if(nums[i]<nums[i+1]){
              firstBreakPoint=i;
              break;
          }
      }

      if(firstBreakPoint!=-1){
          int secondPoint=n-1;
          for(int i=n-1;i>=0;i--){
             if(nums[i]>nums[firstBreakPoint]){
                 secondPoint=i;
                 break;
             }
          }
          
          swap(nums[firstBreakPoint],nums[secondPoint]);
          reverse(nums.begin()+firstBreakPoint+1,nums.end());
      }else{
          reverse(nums.begin(),nums.end());
      }
    }
};
```