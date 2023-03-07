# Interleaving String &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/interleaving-string/)

```
Dynamic Programming
``` 
### Problem Statement 
Given strings s1, s2, and s3, find whether s3 is formed by an interleaving of s1 and s2.

An interleaving of two strings s and t is a configuration where s and t are divided into n and m 
substrings
 respectively, such that:

s = s1 + s2 + ... + sn
t = t1 + t2 + ... + tm
|n - m| <= 1
The interleaving is s1 + t1 + s2 + t2 + s3 + t3 + ... or t1 + s1 + t2 + s2 + t3 + s3 + ...
Note: a + b is the concatenation of strings a and b.


### Sample Input
```
s1 = "aabcc", s2 = "dbbca", s3 = "aadbbcbcac"
```
### Sample Output
```
true
```

### Solution
```cpp
class Solution {
public:
  
    vector<vector<int>>dp;
    
     int solve(int m ,int n,int l,string s1,string s2,string s3){
        if(l==0) return 1;
        if(dp[m][n]!=-1) return dp[m][n];
        
        int a=0,b=0;
        if(m>0 && s1[m-1]==s3[l-1]) a=solve(m-1,n,l-1,s1,s2,s3);
        if(n>0 && s2[n-1]==s3[l-1]) b=solve(m,n-1,l-1,s1,s2,s3);
        
        return dp[m][n]=a||b;
        
    }
    
    
    bool isInterleave(string s1, string s2, string s3) {
        int m=s1.length();
        int n=s2.length();
        int l=s3.length();
        
        dp.resize(m+1,vector<int>(n+1,-1));
        
        if(m+n!=s3.length()) return false;
        
        int ans=solve(m,n,l,s1,s2,s3);
        return ans==1;   
    }
};