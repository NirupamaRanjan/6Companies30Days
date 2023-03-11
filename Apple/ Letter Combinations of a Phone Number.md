
#  Letter Combinations of a Phone Number &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/letter-combinations-of-a-phone-number/description/)

```
String, Backtracking
``` 
### Problem Statement 
Given a string containing digits from 2-9 inclusive, return all possible letter combinations that the number could represent. Return the answer in any order.

A mapping of digits to letters (just like on the telephone buttons) is given below. Note that 1 does not map to any letters.

### Sample Input
```
digits = "23"
```
### Sample Output
```
["ad","ae","af","bd","be","bf","cd","ce","cf"]
```

### Solution
```cpp
class Solution {
public:
   
    
    void solution(string digits,vector<string>&ans,string out,int j,int i){
        
        string given[]={"","","abc","def","ghi","jkl","mno","pqrs","tuv","wxyz"};
        
        if(digits[i]=='\0'){
            out.push_back('\0');
            ans.push_back(out);
            return;
        }
        
        int num=digits[i]-'0';
        string temp=given[num];
    
        for(int k=0;k<temp.length();k++){
            out.push_back(temp[k]);
            solution(digits,ans,out,i+1,j+1);
            out.pop_back();
            
        }        
    }
    
    vector<string> letterCombinations(string digits) {
        
        vector<string>ans;
        if(digits.length()==0) return ans;
        string out;
        solution(digits,ans,out,0,0);
        return ans;
    }
};
```