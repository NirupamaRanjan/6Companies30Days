
# Combinations &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/combinations/description/)

```
Backtracking
``` 
### Problem Statement 
Given two integers n and k, return all possible combinations of k numbers chosen from the range [1, n].

You may return the answer in any order.

### Sample Input
```
n = 4, k = 2
```
### Sample Output
```
[[1,2],[1,3],[1,4],[2,3],[2,4],[3,4]]
```

### Solution
```cpp
class Solution {
public:
    vector<vector<int>>ans;

    void solve(vector<int>temp,int n,int i,int k){

        if(temp.size()==k){
            ans.push_back(temp);
            return;
        }
        
        for(int j=i;j<=n;j++){
            temp.push_back(j);
            solve(temp,n,j+1,k);
            temp.pop_back();
        }
    }

    vector<vector<int>> combine(int n, int k) {
        vector<int>temp;
        solve(temp,n,1,k); 
        return ans;
    }
};
```