
# Find the Index of the First Occurrence in a String &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/find-the-index-of-the-first-occurrence-in-a-string/description/)

```
Array, Two Pointer
``` 
### Problem Statement 
Given two strings needle and haystack, return the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack.

### Sample Input
```
haystack = "sadbutsad", needle = "sad"
```
### Sample Output
```
0
```

### Solution
```cpp
class Solution {
public:
    int strStr(string haystack, string needle) {
          
          int m=haystack.length();
          int n=needle.length();
           if(n>m) return -1;
          
          int i=0,j=0,index=0;

          while(j<m){
             if(i<n && j<m && needle[i]==haystack[j]){
                 i++;
                 j++;
             }else{
                 i=0;
                 index++;
                 j=index; 
             }

             if(i==n) return index;
          }
          
        return -1;        
          
    }
};
```