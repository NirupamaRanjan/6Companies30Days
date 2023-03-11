# Jump Game &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/jump-game/description/)

```
Array, Greedy
``` 
### Problem Statement 
You are given an integer array nums. You are initially positioned at the array's first index, and each element in the array represents your maximum jump length at that position.

Return true if you can reach the last index, or false otherwise.
### Sample Input
```
nums = [2,3,1,1,4]
```
### Sample Output
```
true
```

### Solution
```cpp
class Solution {
public:
    bool canJump(vector<int>& nums) {
        //maximum index upto we can reach
       int canReach=0;
       int n=nums.size();
        for(int i=0;i<nums.size();i++){
            //we reached at i but canReach is less than i it means we cannot reach upto i. so return false
            if(canReach<i) return false;
            //canReach will be maximum of its previous value and max reach from ith index
            canReach=max(canReach,i+nums[i]);
        }
        return true;
    }
};