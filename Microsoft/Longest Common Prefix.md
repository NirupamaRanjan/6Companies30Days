
# Longest Common Prefix &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/longest-common-prefix/description/)

```
String
``` 
### Problem Statement 
Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string "".

### Sample Input
```
strs = ["flower","flow","flight"]
```
### Sample Output
```
Output: "fl"
```

### Solution
```cpp
class Solution {
public:
    string longestCommonPrefix(vector<string>& strs) {
        if(strs.size()==0)   return "";
        string ans;
        int n=strs.size();
        string s=strs[0];
        int i=0;
        int count=0;
        
        while(s[i]!='\0'){
           for(int j=1;j<strs.size();j++){
               string temp=strs[j];
               if(temp[i]==s[i]) count++;
               else break;
           }
            if(count==n-1) ans.push_back(s[i]);
            else break;
            count=0;
            i++;
        }
          
      return ans;
    }
};
```