
# Trapping Rain Water &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/trapping-rain-water/description/)

```
Array, Monotonic stack
``` 
### Problem Statement 
Given n non-negative integers representing an elevation map where the width of each bar is 1, compute how much water it can trap after raining.

### Sample Input
```
height = [0,1,0,2,1,0,1,3,2,1,2,1]
```
### Sample Output
```
6
```

### Solution
```cpp
class Solution {
public:
    int trap(vector<int>& height) {  
        int n=height.size();
        int ans=0;
        int i=0;
        stack<int>st;

        while(i<n){
            
           while(!st.empty() && height[i]>height[st.top()]){
                 int topindex=st.top();
                 st.pop();
                 if(st.empty()) break;

                 int distance=i-st.top()-1;
                 int bound_height=min(height[i],height[st.top()])-height[topindex];
                 ans+=(bound_height*distance);
           }
               st.push(i);
               i++;
        }
        
        return ans;
        
    }
};
```