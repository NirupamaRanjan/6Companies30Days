
# Sum of Two Integers &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/sum-of-two-integers/)

```
Math, Bit Manipulation
``` 
### Problem Statement 
Given two integers a and b, return the sum of the two integers without using the operators + and -.

### Sample Input
```
a = 1, b = 2
```
### Sample Output
```
3
```

### Solution
```cpp
class Solution {
public:
    int getSum(int a, int b) {
        if(b==0) return a;
        return getSum(a^b, (unsigned)(a&b)<<1);
    }
};
```