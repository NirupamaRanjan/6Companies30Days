
# Longest Valid Parentheses &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/longest-valid-parentheses/)

```
String, Stack
``` 
### Problem Statement 
Given a string containing just the characters '(' and ')', return the length of the longest valid (well-formed) parentheses substring.

### Sample Input
```
s = "(()"
```
### Sample Output
```
2
```

### Solution
```cpp
class Solution {
public:
    int longestValidParentheses(string s) {
        stack<int>st;
        st.push(-1);
        int ans=0;
        for(int i=0;i<s.length();i++){
            if(s[i]=='('){
                st.push(i);
            }
           else{
               st.pop();
               if(!st.empty()) ans=max(ans,i-st.top());
               else st.push(i);
           } 
        }
        
        return ans;
    }
};
```