
# Largest Number &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/largest-number/description/)

```
Array, Sorting
``` 
### Problem Statement 
Given a list of non-negative integers nums, arrange them such that they form the largest number and return it.

Since the result may be very large, so you need to return a string instead of an integer.
### Sample Input
```
nums = [3,30,34,5,9]
```
### Sample Output
```
"9534330"
```

### Solution
```cpp
class Solution {
public:
    static bool mycomp(int  a,int b){
        string s1=to_string(a);
        string s2=to_string(b);

        return s1+s2>=s2+s1;
    }

    string largestNumber(vector<int>& nums) {
      string ans="";
      int count=0;

      for(int i=0;i<nums.size();i++){
        if(nums[i]==0) count++;
      }
      if(count==nums.size()) return "0";

      sort(nums.begin(),nums.end(),mycomp);
      int i=0;
      while(i<nums.size()){
        ans+=(to_string(nums[i]));
        i++;
      }
      
      return  ans;
      
    }
};
```