
# Insert Interval &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/insert-interval/description/)

```
Array, Sorting, Binary Search
``` 
### Problem Statement 
You are given an array of non-overlapping intervals intervals where intervals[i] = [starti, endi] represent the start and the end of the ith interval and intervals is sorted in ascending order by starti. You are also given an interval newInterval = [start, end] that represents the start and end of another interval.

Insert newInterval into intervals such that intervals is still sorted in ascending order by starti and intervals still does not have any overlapping intervals (merge overlapping intervals if necessary).

Return intervals after the insertion.
### Sample Input
```
intervals = [[1,3],[6,9]], newInterval = [2,5]
```
### Sample Output
```
[[1,5],[6,9]]
```

### Solution
```cpp
class Solution {
public:
    vector<vector<int>> insert(vector<vector<int>>& intervals, vector<int>& newInterval) {
        vector<vector<int>>ans;
      
        int index=upper_bound(intervals.begin(),intervals.end(),newInterval)-intervals.begin();
        if(index!=intervals.size()){
            intervals.insert(intervals.begin()+index,newInterval);
        }else{
            intervals.push_back(newInterval);
        }

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