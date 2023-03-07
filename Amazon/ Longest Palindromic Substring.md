# Longest Palindromic Substring &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/longest-palindromic-substring/)

```
String, Dynamic Programming
``` 
### Problem Statement 
Given a string s, return the longest palindromic substring in s.
### Sample Input
```
s = "babad"
```
### Sample Output
```
"bab"
```

### Solution
```cpp
class Solution {
public:
    string longestPalindrome(string s) {
        int n=s.length();
        vector<vector<int>>dp(n,vector<int>(n,0));
        
        int st=0,e=0;
        int l=1;
        for(int i=0;i<n;i++){
            dp[i][i]=1;
        }
        
        for(int j=1;j<n;j++){
            if(s[j]==s[j-1]){
                dp[j-1][j]=1;
                st=j-1;
                e=j;
                l=2;
            }
        }
        
        for(int length=3;length<=n;length++){
            int i=0;
            for(int j=length-1;j<n;j++){
                if(s[j]==s[i] && dp[i+1][j-1]){
                    dp[i][j]=1;
                    st=i;
                    e=j;
                    l=length;
                }
                
                i++;
            }
        }
        
        string ans="";
        for(int i=st;i<=e;i++){
            ans.push_back(s[i]);
        }
        return ans;
        
    }
};