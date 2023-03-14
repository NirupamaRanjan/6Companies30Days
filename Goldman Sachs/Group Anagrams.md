
#  Group Anagrams &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/group-anagrams/description/)

```
Array, String, Hash Table, Sorting
``` 
### Problem Statement 
Given an array of strings strs, group the anagrams together. You can return the answer in any order.

An Anagram is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

### Sample Input
```
strs = ["eat","tea","tan","ate","nat","bat"]
```
### Sample Output
```
[["bat"],["nat","tan"],["ate","eat","tea"]]
```

### Solution
```cpp
class Solution {
public:
    vector<vector<string>> groupAnagrams(vector<string>& strs) {
        
        vector<vector<string>>ans;
        unordered_map<string,vector<string>>mp;
        
        //O(nllogl)
        //n: size of strs , l:length of strs[i]
        for(int i=0;i<strs.size();i++){
            string temp=strs[i];
            sort(temp.begin(),temp.end()); 
            mp[temp].push_back(strs[i]);
            
        }

        //O(n)
        for(auto x: mp){
            ans.push_back(x.second);
        }

        return ans;
        
    }
};
```