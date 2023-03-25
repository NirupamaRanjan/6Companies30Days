
# Minimum Window Substring &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/minimum-window-substring/)

```
Array, Sliding Window, Hash table
``` 
### Problem Statement 
Given two strings s and t of lengths m and n respectively, return the minimum window 
substring
 of s such that every character in t (including duplicates) is included in the window. If there is no such substring, return the empty string "".

The testcases will be generated such that the answer is unique.

### Sample Input
```
s = "ADOBECODEBANC", t = "ABC"
```
### Sample Output
```
"BANC"
```

### Solution
```cpp
class Solution {
public:
    string minWindow(string s, string t) {
        int m=s.length();
        int n=t.length();
        string ans="";
        
        if(n>m) return "";
        
        unordered_map<char,int>f;
        for(auto x:t) f[x]++;
        int count=f.size();
        
        
        int i=0,j=0,len=INT_MAX;
        
        // Finding the first index in s which matches with any character of string t
        while(i<m && f.find(s[i])==f.end()) i++;
    
        if(i==m) return "";   // Means not a single character is matching
        
        while(j<m){
            if(f.find(s[j])!=f.end()){
                f[s[j]]--;
                if(f[s[j]]==0) count--;
            }
            
            //Candidate substring
            if(count==0){   
                if(j-i+1<len){
                    len=(j-i+1);
                    ans=s.substr(i,j-i+1);
                }
                
                while(count==0){
                        f[s[i]]++;
                        if(f[s[i]]>0) count++;
                        i++;
                        while(i<m && f.find(s[i])==f.end()) i++;
                       //candidate substring
                        if(count==0){
                              if(j-i+1<len){
                                len=(j-i+1);
                                ans=s.substr(i,j-i+1);
                                } 
                          }
                  } 
               }
            
            j++;
            
            
        }
        
        return ans;
    }
};
```