
# Merge Intervals &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/merge-intervals/description/)

```
Array,Sorting
``` 
### Problem Statement 
Given an array of intervals where intervals[i] = [starti, endi], merge all overlapping intervals, and return an array of the non-overlapping intervals that cover all the intervals in the input.
### Sample Input
```
intervals = [[1,3],[2,6],[8,10],[15,18]]
```
### Sample Output
```
[[1,6],[8,10],[15,18]]
```

### Solution
```cpp
class Solution {
public:
    vector<vector<int>> merge(vector<vector<int>>& intervals) {
        sort(intervals.begin(),intervals.end());
        vector<vector<int>>ans;
        pair<int,int>p=make_pair(intervals[0][0],intervals[0][1]);

        for(int i=0;i<intervals.size();i++){
               
                 if(intervals[i][0]<=p.second){
                     //check if it merges or completely lie inside p
                     if(intervals[i][1]<=p.second){
                         //it lies inside p
                         continue;
                     }else{
                         //merge it with p
                         p.second=intervals[i][1];
                     }
                 }else{
                     //lies outside p
                     ans.push_back({p.first,p.second});
                     //update p
                     p.first=intervals[i][0];
                     p.second=intervals[i][1];
                 }
        }

        ans.push_back({p.first,p.second});
        return ans;
    }
};
```