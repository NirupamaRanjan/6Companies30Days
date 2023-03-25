
# Count and Say &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/count-and-say/description/)

```
String
``` 
### Problem Statement 
The count-and-say sequence is a sequence of digit strings defined by the recursive formula:

countAndSay(1) = "1"
countAndSay(n) is the way you would "say" the digit string from countAndSay(n-1), which is then converted into a different digit string.
To determine how you "say" a digit string, split it into the minimal number of substrings such that each substring contains exactly one unique digit. Then for each substring, say the number of digits, then say the digit. Finally, concatenate every said digit.

Given a positive integer n, return the nth term of the count-and-say sequence.

 
### Sample Input
```
n = 4
```
### Sample Output
```
"1211"
```

### Solution
```cpp
class Solution {
public:
    
    void helper(string &s,int n){
        if(n==0) return;
        
        int l=s.length();
        string temp=s;
        s.erase(s.begin(),s.end());
        int i=0;
        
        while(i<l){
            int count=1;
            char c=temp[i];
            while(i<l-1 && temp[i]==temp[i+1]){
                count++;
                i++;
            }
          s.push_back(count+'0');
          s.push_back(c);
          i++;
        }
        
        helper(s,n-1);
    }
    
    
    string countAndSay(int n) {
        string s="1";
        //n-1 because we have string for n=1  already
        helper(s,n-1);
        return s;
    }
};
```