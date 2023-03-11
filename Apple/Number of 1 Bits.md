
# Number of 1 Bits &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/number-of-1-bits/)

```
Bit Manipulation
``` 
### Problem Statement 
Write a function that takes the binary representation of an unsigned integer and returns the number of '1' bits it has (also known as the Hamming weight).

Note:

Note that in some languages, such as Java, there is no unsigned integer type. In this case, the input will be given as a signed integer type. It should not affect your implementation, as the integer's internal binary representation is the same, whether it is signed or unsigned.
In Java, the compiler represents the signed integers using 2's complement notation. Therefore, in Example 3, the input represents the signed integer. -3.

### Sample Input
```
n = 00000000000000000000000000001011
```
### Sample Output
```
 3
```

### Solution
```cpp
class Solution {
public:
    int hammingWeight(uint32_t n) {
        int ans=0;
        while(n){
            if(n&1) ans++;
            n=n>>1;
        }
        return ans;
    }
};