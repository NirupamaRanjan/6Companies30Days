
# Shuffle the Array &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/shuffle-the-array/description/)

```
Array, Two pointer
``` 
### Problem Statement 
Given the array nums consisting of 2n elements in the form [x1,x2,...,xn,y1,y2,...,yn].

Return the array in the form [x1,y1,x2,y2,...,xn,yn].


### Sample Input
```
nums = [2,5,1,3,4,7], n = 3
```
### Sample Output
```
[2,3,5,4,1,7] 
```

### Solution
```cpp
class Solution {
public:
    vector<int> shuffle(vector<int>& nums, int n) {
          int j=0;

          for(int i=0;i<2*n;i+=2){
              nums[i]+=(nums[j]%10000)*10000;
              nums[i+1]+=(nums[j+n]%10000)*10000;
              j++;
          }

          for(int i=0;i<2*n;i++){
              nums[i]/=10000;
          }

          return nums;
    }
};
```