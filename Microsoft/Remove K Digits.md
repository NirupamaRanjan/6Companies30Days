
# Remove K Digits &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/remove-k-digits/description/)

```
Array, Stack
``` 
### Problem Statement 
Given string num representing a non-negative integer num, and an integer k, return the smallest possible integer after removing k digits from num.

### Sample Input
```
num = "1432219", k = 3
```
### Sample Output
```
"1219"
```

### Solution
```cpp
class Solution {
public:
    string removeKdigits(string num, int k) {
         int n=num.size();
        string ans="";
        if(n==k) return "0";
        if(n==0) return "0";
        int i=0;

        stack<char>s;
        s.push(num[0]);

        for(int i=1;i<n;i++){
            while(k>0 && !s.empty() && num[i]<s.top()){
                s.pop();
                k--;
            }
            s.push(num[i]); 
            //remove zeroes from start
            if(s.size()==1 && num[i]=='0') s.pop();  
        }
        
        // for strings sorted in ascending order
        while(k && !s.empty()){
             s.pop();
             k--;
        }

        while(!s.empty()){
            ans.push_back(s.top());
            s.pop();
        }
        reverse(ans.begin(),ans.end());
        return ans.length()==0? "0" : ans;
        

    }
};
```