
# Plus One &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/plus-one/description/)

```
Array
``` 
### Problem Statement 
You are given a large integer represented as an integer array digits, where each digits[i] is the ith digit of the integer. The digits are ordered from most significant to least significant in left-to-right order. The large integer does not contain any leading 0's.

Increment the large integer by one and return the resulting array of digits.
 
### Sample Input
```
digits = [1,2,3]
```
### Sample Output
```
[1,2,4]
```

### Solution
```cpp
class Solution {
public:
    vector<int> plusOne(vector<int>& digits) {
        for(int i=digits.size()-1;i>=0;i--){
            if(digits[i]!=9){
                digits[i]++;
                return digits;
            }else{
                digits[i]=0;
            }
           
        }
        //digits is 000000. so push 1 and reverse it
         digits.push_back(1);
         reverse(digits.begin(),digits.end());
        return digits;
    }
};
```