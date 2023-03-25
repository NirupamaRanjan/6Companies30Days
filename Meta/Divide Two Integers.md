
# Divide Two Integers &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/divide-two-integers/)

```
Math
``` 
### Problem Statement 
Given two integers dividend and divisor, divide two integers without using multiplication, division, and mod operator.

The integer division should truncate toward zero, which means losing its fractional part. For example, 8.345 would be truncated to 8, and -2.7335 would be truncated to -2.

Return the quotient after dividing dividend by divisor.

Note: Assume we are dealing with an environment that could only store integers within the 32-bit signed integer range: [−231, 231 − 1]. For this problem, if the quotient is strictly greater than 231 - 1, then return 231 - 1, and if the quotient is strictly less than -231, then return -231.

### Sample Input
```
dividend = 10, divisor = 3
```
### Sample Output
```
3
```

### Solution
```cpp
class Solution {
public:
    int divide(int dividend, int divisor) {
        
      if(dividend==INT_MIN && divisor==-1) return INT_MAX;
        
       long dvd=labs(dividend), dvs=labs(divisor);
       int sign=1;
       long ans=0;

       //taking xor of dividend>0 and divisor>0 to cover all four cases
       if(dividend>0^divisor>0){
            sign=-1;   
       }
        
        while(dvd>=dvs){
            // m is the multiplier
            long temp=dvs,m=1;
            while(temp<<1 <=dvd){
                temp=temp<<1;
                m=m<<1;
            }
            
            dvd-=temp;
            ans+=m;
        }
        
        return ans*sign;
    }
};
```