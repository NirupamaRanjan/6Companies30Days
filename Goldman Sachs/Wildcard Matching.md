
# Wildcard Matching &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/wildcard-matching/description/)

```
String, Dynamic Programming
``` 
### Problem Statement 
Given an input string (s) and a pattern (p), implement wildcard pattern matching with support for '?' and '*' where:

'?' Matches any single character.
'*' Matches any sequence of characters (including the empty sequence).
The matching should cover the entire input string (not partial).


### Sample Input
```
s = "aa", p = "a"
```
### Sample Output
```
false
```

### Solution
```cpp
class Solution {
public:
    vector<vector<bool>>dp;

    bool isMatch(string s, string p) {
        int l1=s.length();
        int l2=p.length();

        dp.resize(l1+1,vector<bool>(l2+1,false));

        dp[0][0]=true;

        for(int i=1;i<=l1;i++){
            dp[i][0]=false;
        }

        for(int j=1;j<=l2 ;j++){
            bool flag=true;
            for(int k=1; k<=j ;k++){
                 if(p[k-1]!='*') {
                     flag=false;
                 }
             }

             dp[0][j]=flag;
        }

        for(int i=1;i<=l1;i++){
            for(int j=1;j<=l2;j++){
                 if(s[i-1]==p[j-1] || p[j-1]=='?') dp[i][j]=dp[i-1][j-1];
                 else if(p[j-1]=='*') dp[i][j]=dp[i][j-1]|| dp[i-1][j];
         
            }
        }
       return dp[l1][l2];
    }
};
```