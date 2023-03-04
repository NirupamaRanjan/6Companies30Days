# Valid Parentheses &ensp;   [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/valid-parentheses/)

```
String, Stack
``` 
### Problem Statement 

Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

An input string is valid if:

Open brackets must be closed by the same type of brackets.
Open brackets must be closed in the correct order.
Every close bracket has a corresponding open bracket of the same type.


### Sample Input
```
s = "()[]{}"
```
### Sample Output
```
true
```

### Solution
```cpp
class Solution {
public:
    bool isValid(string s) {
        stack<char>st;
        
        for(int i=0;i<s.length();i++){
            if(st.empty()) st.push(s[i]);
            
            else if((st.top()=='('  && s[i]==')')  || (st.top()=='{'  && s[i]=='}')|| (st.top()=='['  && s[i]==']') )
                st.pop();
            
            else st.push(s[i]);
            
        }
        
        if(st.empty()) return true;
        else return false;
    }
};
`