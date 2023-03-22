
#  Pow(x, n) &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/powx-n/description/)

```
Math
``` 
### Problem Statement 
Implement pow(x, n), which calculates x raised to the power n (i.e., xn).
### Sample Input
```
x = 2.00000, n = 10
```
### Sample Output
```
1024.00000
```

### Solution
```cpp
class Solution {
public:
     
    double power(double x,long p){
        double ans=1;
        while(p){
            if(p&1)  ans*=x;
            x*=x;
            p=p>>1;
        }
        return ans;
    }
    
    double myPow(double x, int n) {
        cout<<fixed<<setprecision(5);
        long p=abs((long)n);
        double ans=power(x,p);
        return n<0?(1/ans):ans;
    }
};
```