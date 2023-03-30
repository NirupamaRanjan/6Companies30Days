
# Simplify Path &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/simplify-path/description/)

```
Array, Stack
``` 
### Problem Statement 
Given a string path, which is an absolute path (starting with a slash '/') to a file or directory in a Unix-style file system, convert it to the simplified canonical path.

In a Unix-style file system, a period '.' refers to the current directory, a double period '..' refers to the directory up a level, and any multiple consecutive slashes (i.e. '//') are treated as a single slash '/'. For this problem, any other format of periods such as '...' are treated as file/directory names.

The canonical path should have the following format:

The path starts with a single slash '/'.
Any two directories are separated by a single slash '/'.
The path does not end with a trailing '/'.
The path only contains the directories on the path from the root directory to the target file or directory (i.e., no period '.' or double period '..')
Return the simplified canonical path.
### Sample Input
```
path = "/home//foo/"
```
### Sample Output
```
"/home/foo"
```

### Solution
```cpp
class Solution {
public:
    string simplifyPath(string path) {
        //'.' means stay in the currfolder
        //'..' means get out from the currfolder 
 
        int n=path.length();
        int i=0;
        string ans="";

        vector<string>v;
        stack<string>st;
        
        //split the path on the delimiter '/'
        while(i<n){
           while(i<n && path[i]=='/') i++;
           string temp="";
           while(i<n && path[i]!='/'){
                temp.push_back(path[i]);
                i++;
           } 
           if(temp!="") v.push_back(temp);
        }
         
         //pop when to get out 
        for(int j=0;j<v.size();j++){
            if(!st.empty() && v[j]=="..") st.pop();
            else if(v[j]!="." && v[j]!="..") st.push(v[j]);
        }
        
        
        if(st.empty()) return "/";

        while(!st.empty()){
            ans.insert(0,"/"+st.top());
            st.pop();
           
        }
              
        return  ans;
    }
};
```