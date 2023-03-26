
# Sort Colors &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/sort-colors/description/)

```
Sorting
``` 
### Problem Statement 
Given an array nums with n objects colored red, white, or blue, sort them in-place so that objects of the same color are adjacent, with the colors in the order red, white, and blue.

We will use the integers 0, 1, and 2 to represent the color red, white, and blue, respectively.

You must solve this problem without using the library's sort function.

 
### Sample Input
```
nums = [2,0,2,1,1,0]
```
### Sample Output
```
[0,0,1,1,2,2]
```

### Solution
```cpp
class Solution {
public:
    void sortColors(vector<int>& a) {
        int n=a.size();
        int  i=0,j=0,k=n-1;
        
        while(k>=j){
            if(a[j]==0){
                swap(a[i],a[j]);  
                 i++;
                 j++;
                
            }else if(a[j]==1){
                j++;
            }else {
                swap(a[j],a[k]);
                k--;
            }
        }
    }
};
```