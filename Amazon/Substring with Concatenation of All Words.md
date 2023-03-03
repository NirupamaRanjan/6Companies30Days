# Substring with Concatenation of All Words[![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/substring-with-concatenation-of-all-words/)

```
Hash map, Sliding Window
``` 
### Problem Statement 

You are given a string s and an array of strings words. All the strings of words are of the same length.

A concatenated substring in s is a substring that contains all the strings of any permutation of words concatenated.

For example, if words = ["ab","cd","ef"], then "abcdef", "abefcd", "cdabef", "cdefab", "efabcd", and "efcdab" are all concatenated strings. "acdbef" is not a concatenated substring because it is not the concatenation of any permutation of words.
Return the starting indices of all the concatenated substrings in s. You can return the answer in any order.

### Sample Input
```
s = "barfoothefoobarman", words = ["foo","bar"]
```
### Sample Output
```
[0,9]
```

### Solution
```cpp
class Solution {
public:
    vector<int> findSubstring(string s, vector<string>& words) {
        vector<int>ans;
        int l=words[0].length();
        int n=words.size();
        int i=0,j=n*l-1;

        if(s.length()<n*l) return ans;

        unordered_map<string,int>mp;
       
        for(int i=0;i<words.size();i++){
            mp[words[i]]++;
        }

        while(j<s.length()){
            bool flag=false;
             unordered_map<string,int>mp2;

            for(int k=i;k<=j;k+=l){
                string temp=s.substr(k,l);
                mp2[temp]++;
            }

            for(auto x: mp){
                if(mp[x.first]!=mp2[x.first]){
                    flag=true;
                    break;
                }
            }

            if(!flag) ans.push_back(i);

            i++;
            j++;

        }
    
        
    return ans;

    }
};
`