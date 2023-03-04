# Majority Element[![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/majority-element/description/)

```
Array, Counting
``` 
### Problem Statement 

Given an array nums of size n, return the majority element.

The majority element is the element that appears more than ⌊n / 2⌋ times. You may assume that the majority element always exists in the array.

### Sample Input
```
nums = [2,2,1,1,1,2,2]
```
### Sample Output
```
2
```

### Solution
```cpp
class Solution {
public:
    int majorityElement(vector<int>& nums) {
        int n=nums.size();
        int ce=nums[0];
        int count=1;
        for(int i=1;i<n;i++){
            if(nums[i]==ce){
                count++;
            }else{
                count--;
                if(count==0){
                    ce=nums[i];
                    count=1;
                }
            }
        }
        return ce;
    }
};
`