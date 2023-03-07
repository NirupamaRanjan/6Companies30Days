# Kth Largest Element in an Array &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/kth-largest-element-in-an-array/)

```
Array, Priority Queue
``` 
### Problem Statement 
Given an integer array nums and an integer k, return the kth largest element in the array.

Note that it is the kth largest element in the sorted order, not the kth distinct element.

You must solve it in O(n) time complexity.
### Sample Input
```
nums = [3,2,1,5,6,4], k = 2
```
### Sample Output
```
5
```

### Solution
```cpp
class Solution {
public:
    int findKthLargest(vector<int>& nums, int k) {
       priority_queue<int,vector<int>,greater<int>>pq;
       for(int i=0;i<k;i++){
           pq.push(nums[i]);
       }
        
        for(int i=k;i<nums.size();i++){
            if(nums[i]>pq.top()) {
                pq.pop();
                pq.push(nums[i]);
            }
        }
        
        return pq.top();
    }
};