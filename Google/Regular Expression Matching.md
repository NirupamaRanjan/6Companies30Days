
# Regular Expression Matching &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/regular-expression-matching/description/)

```
String, Dynamic Programming
``` 
### Problem Statement 
Given an input string s and a pattern p, implement regular expression matching with support for '.' and '*' where:

'.' Matches any single character.​​​​
'*' Matches zero or more of the preceding element.
The matching should cover the entire input string (not partial).

### Sample Input
```
s = "aa", p = "a*"
```
### Sample Output
```
true
```

### Solution
```cpp
class Solution {
public:
    
    bool isMatch(string s, string p) {
        int n1=s.length();
        int n2=p.length();
        
        vector<vector<bool>>dp(n2+1,vector<bool>(n1+1,false));
        
        dp[0][0]=true; 
        
        for(int i=2;i<=n2;i++){
            if(p[i-1]=='*') dp[i][0]=dp[i-2][0];
        }
        
       
        for(int i=1;i<=n2;i++){
            for(int j=1;j<=n1;j++)
            {
                 if(p[i-1]==s[j-1])    dp[i][j]=dp[i-1][j-1];
                 else if(p[i-1]=='.')  dp[i][j]=dp[i-1][j-1];
                 else if(p[i-1]=='*')
                      {
                        if(dp[i-2][j]==true) dp[i][j]=true;
                        else if(s[j-1]==p[i-2] ||p[i-2]=='.')  dp[i][j]=dp[i][j-1];
                       }
                 }
            }
        
        return dp[n2][n1];
       
    }
    
};
```