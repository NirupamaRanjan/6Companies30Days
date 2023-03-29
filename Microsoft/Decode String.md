
# Decode String &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/decode-string/description/)

```
String, Stack
``` 
### Problem Statement 
Given an encoded string, return its decoded string.

The encoding rule is: k[encoded_string], where the encoded_string inside the square brackets is being repeated exactly k times. Note that k is guaranteed to be a positive integer.

You may assume that the input string is always valid; there are no extra white spaces, square brackets are well-formed, etc. Furthermore, you may assume that the original data does not contain any digits and that digits are only for those repeat numbers, k. For example, there will not be input like 3a or 2[4].

The test cases are generated so that the length of the output will never exceed 105.

### Sample Input
```
s = "3[a]2[bc]"
```
### Sample Output
```
"aaabcbc"
```

### Solution
```cpp
class Solution {
public:
    string decodeString(string s) {
        int n=s.length();
        int i=0;
        stack<string>st;

        string currString="";
        string currNumber="";

        while(i<n){
            if(s[i]=='['){
              i++;
            }

            if(s[i]==']'){
               int num=stoi(st.top());
               st.pop();
               string prevString="";

               if(!st.empty()){
                   prevString=st.top();
                   st.pop();
               }
               string temp=currString;

               for(int i=1;i<num;i++){
                    currString+=temp;
               }
               //basic 
               currString=prevString+currString;
               i++;

            }else if(s[i]>='0' && s[i]<='9'){
                 st.push(currString);
                 currString="";
                 
                  // for numbers greter than 9
                 while(i<n && s[i]>='0' && s[i]<='9'){
                    currNumber.push_back(s[i]);
                    i++;
                 }
                 st.push(currNumber);
                 currNumber="";
                
            }else {
                 currString.push_back(s[i]); 
                 i++;
            }
        }

       return currString;

    }
};
```