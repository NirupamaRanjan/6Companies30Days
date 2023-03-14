
# Container With Most Water &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/container-with-most-water/)

```
Array, Two Pointers
``` 
### Problem Statement 
You are given an integer array height of length n. There are n vertical lines drawn such that the two endpoints of the ith line are (i, 0) and (i, height[i]).

Find two lines that together with the x-axis form a container, such that the container contains the most water.

Return the maximum amount of water a container can store.

Notice that you may not slant the container.

 

### Sample Input
```
height = [1,8,6,2,5,4,8,3,7]
```
### Sample Output
```
49
```

### Solution
```cpp
class Solution {
public:
    int maxArea(vector<int>& height) {
         int n=height.size();
        
        int s=0;
        int e=n-1;
        int area=0;
        if(s==e) return 0;
        while(e>s){
            int h=min(height[s],height[e]);
         area=max(area,h*(e-s));
            if(height[s]>height[e])  e--;
            else s++;
        }
        
        return area;
    }
};
```