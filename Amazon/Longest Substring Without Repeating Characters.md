# Longest Substring Without Repeating Characters &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/longest-substring-without-repeating-characters/description/)

```
Hash Table, Sliding Window, String
``` 
### Problem Statement 
Given a string s, find the length of the longest substring without repeating characters.

### Sample Input
```
"abcabcbb"
```
### Sample Output
```
3
```

### Solution
```cpp
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        unordered_map<char,int>m;
        int i=0,j=0;
        int ans=INT_MIN;
        int n=s.length();
        while(j<n){
            m[s[j]]++;
            if(m.size()<j-i+1){
               ans=max(ans,j-i);
               while(m[s[j]]>1){
                   m[s[i]]--;
                   if(m[s[i]]==0) m.erase(s[i]);
                   i++;                  
               }
            }
          j++;
            
        }
        j--;
        while(i<n && m[s[j]]>1){
            m[s[i]]--;
            i++;
        }
        
        return ans=max(ans,j-i+1);
    }
};