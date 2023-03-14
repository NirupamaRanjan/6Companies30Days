
# Median of Two Sorted Arrays &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/median-of-two-sorted-arrays/description/)

```
Array, Binary Search
``` 
### Problem Statement 
Given two sorted arrays nums1 and nums2 of size m and n respectively, return the median of the two sorted arrays.

The overall run time complexity should be O(log (m+n)).
### Sample Input
```
nums1 = [1,3], nums2 = [2]
```
### Sample Output
```
2.00000
```

### Solution
```cpp
class Solution {
public:
    double findMedianSortedArrays(vector<int>& nums1, vector<int>& nums2) {
        //First approach 
        //store nums1 and nums2 in a vector of size(m+n)
        //sort the array 
        // find the median

        if(nums1.size()>nums2.size()) return findMedianSortedArrays(nums2,nums1);// try to do binary search in smaller array
        int n=nums1.size();
        int m=nums2.size();

        int s=0,e=n;

        while(s<=e){
            int mid=s+(e-s)/2;
            int mid2=(n+m+1)/2-mid;

            int l1=mid==0? INT_MIN : nums1[mid-1];
            int l2=mid2==0? INT_MIN : nums2[mid2-1];

            int r1=mid==n ? INT_MAX :nums1[mid];
            int r2=mid2==m ? INT_MAX : nums2[mid2];

            if(l1<=r2 && l2<=r1){
                if((n+m)%2){
                    return max(l1,l2);
                }else{
                    return (max(l1,l2)+min(r1,r2))/2.0;
                }
            }

            if(l1>r2){
                e=mid-1;
            }else{
                s=mid+1;
            }
        }
        
        return 0.0;
       
    }
};
```