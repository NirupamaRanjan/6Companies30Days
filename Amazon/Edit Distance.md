# Edit Distance

### Dynamic Programming

### Problem Statement 

[![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/edit-distance/)

Given two strings word1 and word2, return the minimum number of operations required to convert word1 to word2.

You have the following three operations permitted on a word:

1.Insert a character
2.Delete a character
3.Replace a character

### Sample Input
```
word1 = "horse", word2 = "ros"
```
### Sample Output
```
"3"
```

### Solution
```cpp
class Solution {
public:
    int minDistance(string word1, string word2) {
        int m=word1.length();
        int n=word2.length();
        
        vector<vector<int>>dp(m+1,vector<int>(n+1,0));
        
        
        for(int i=0;i<=m;i++) dp[i][0]=i;
        for(int j=0;j<=n;j++) dp[0][j]=j;
        
        for(int i=1;i<=m;i++){
            for(int j=1;j<=n;j++){
                if(word1[i-1]==word2[j-1]){
                    dp[i][j]=dp[i-1][j-1];
                }else{
                    dp[i][j]=1+min({dp[i-1][j-1],dp[i][j-1],dp[i-1][j]});
                }
            }
        }
        
        return dp[m][n];
    }
};
`