
# Frog Jump &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/frog-jump/description/)

```
Array, Dynamic Programming
``` 
### Problem Statement 
A frog is crossing a river. The river is divided into some number of units, and at each unit, there may or may not exist a stone. The frog can jump on a stone, but it must not jump into the water.

Given a list of stones' positions (in units) in sorted ascending order, determine if the frog can cross the river by landing on the last stone. Initially, the frog is on the first stone and assumes the first jump must be 1 unit.

If the frog's last jump was k units, its next jump must be either k - 1, k, or k + 1 units. The frog can only jump in the forward direction.

### Sample Input
```
stones = [0,1,3,5,6,8,12,17]
```
### Sample Output
```
true
```

### Solution
```cpp
class Solution {
public:
    map<pair<int,int>,bool>dp; ///why not unordered_map

   bool solve(int j,int i,vector<int>& stones){
       if(i==stones.size()-1) return true;
       if(i>=stones.size()) return false;

       if(dp.find({i,j})!=dp.end())  return dp[{i,j}];

       bool res=false;

       int nexti=lower_bound(stones.begin(),stones.end(),stones[i]+j+1)-stones.begin();
       if(nexti!=stones.size() && stones[nexti]==stones[i]+j+1) res=solve(j+1,nexti,stones);   
       if(res) return dp[{i,j}]=true;

       nexti=lower_bound(stones.begin(),stones.end(),stones[i]+j)-stones.begin();
       if(j && nexti!=stones.size() && stones[nexti]==stones[i]+j) res=solve(j,nexti,stones);
       if(res) return dp[{i,j}]=true;

      nexti=lower_bound(stones.begin(),stones.end(),stones[i]+j-1)-stones.begin();
       if(j-1 && nexti!=stones.size() && stones[nexti]==stones[i]+j-1){
           res=solve(j-1,nexti,stones);
           if(res) return dp[{i,j}]=true;
       }

       return dp[{i,j}]=res;
   }

    bool canCross(vector<int>& stones) {
       return solve(0,0,stones);
    }
};
```