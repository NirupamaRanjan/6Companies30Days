
# Generate Parentheses &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/generate-parentheses/description/)

```
String,Backtracking
``` 
### Problem Statement 
Given n pairs of parentheses, write a function to generate all combinations of well-formed parentheses.
### Sample Input
```
 n = 3
```
### Sample Output
```
["((()))","(()())","(())()","()(())","()()()"]
```

### Solution
```cpp
class Solution {  
public:
    vector<string>v;
    
    void solution(int n,int o,int c,string ans){
        if(ans.length()==2*n){
            v.push_back(ans);
            return;
        }
        
        if(o==c || o<n){
        ans.push_back('(');
        solution(n,o+1,c,ans);
        ans.pop_back();
        }
        
        
        if(o>c){
        ans.push_back(')');
        solution(n,o,c+1,ans);
        ans.pop_back();
        }    
        
        
    }
    
    vector<string> generateParenthesis(int n) {
        
        solution(n,0,0,"");
        return v;
    }
};
```