
# First Unique Character in a String &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/first-unique-character-in-a-string/description/)

```
String, Hash table, Queue
``` 
### Problem Statement 
Given a string s, find the first non-repeating character in it and return its index. If it does not exist, return -1.

### Sample Input
```
s = "loveleetcode"
```
### Sample Output
```
2
```

### Solution
```cpp
class Solution {
public:
    int firstUniqChar(string s) {
        unordered_map<char,int>m;
        int n=s.length();
        
        for(int i=0;i<n;i++){
            m[s[i]]++;
        }
        
        for(int i=0;i<n;i++)
            if(m[s[i]]==1) return i;
        
        return -1;
    }
};
```