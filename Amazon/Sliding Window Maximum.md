# Sliding Window Maximum[![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/sliding-window-maximum/)

```
Sliding Window, Queue
``` 
### Problem Statement 

You are given an array of integers nums, there is a sliding window of size k which is moving from the very left of the array to the very right. You can only see the k numbers in the window. Each time the sliding window moves right by one position.

Return the max sliding window.

### Sample Input
```
nums = [1,3,-1,-3,5,3,6,7], k = 3
```
### Sample Output
```
[3,3,5,5,6,7]
```

### Solution
```cpp
class Solution {
public:
    vector<int> maxSlidingWindow(vector<int>& nums, int k) {
        vector<int>ans;
       int n=nums.size();
       int i=0;
       deque<int>q;
      
       while(i<n && i<k){
          while(!q.empty() && nums[i]>nums[q.back()]){
              //for this step we took deque and not simple queue
              q.pop_back();
          }
          q.push_back(i);
          i++;
       }

      ans.push_back(nums[q.front()]);

       while(i<n){
          while(!q.empty() && q.front()<i-k+1) q.pop_front();
          
          while(!q.empty() && nums[i]>nums[q.back()]){
              //for this step we took deque and not simple queue
              q.pop_back();
          }
          

          q.push_back(i);
          ans.push_back(nums[q.front()]);
          i++;
       }

       return ans;
    }
};
`
