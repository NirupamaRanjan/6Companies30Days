
# Top K Frequent Elements &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/top-k-frequent-elements/description/)

```
Array, heap
``` 
### Problem Statement 
Given an integer array nums and an integer k, return the k most frequent elements. You may return the answer in any order.


### Sample Input
```
nums = [1,1,1,2,2,3], k = 2
```
### Sample Output
```
[1,2]
```

### Solution
```cpp
class Solution {
public:
    vector<int> topKFrequent(vector<int>& nums, int k) {
          unordered_map<int,int>m;
          for(int i=0;i<nums.size();i++){
              m[nums[i]]++;
          }
        
          priority_queue<pair<int,int>>q;
        
          for(auto x:m){
              q.push({x.second,x.first});
          }
        
        int count=0;
        vector<int>ans;
        while(count<k){
            ans.push_back(q.top().second);
            q.pop();
            count++;
        }
        return ans;
    }
};
```