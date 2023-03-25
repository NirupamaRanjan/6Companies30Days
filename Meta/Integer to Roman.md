
# Integer to Roman &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/integer-to-roman/)

```
Array
``` 
### Problem Statement 
Roman numerals are represented by seven different symbols: I, V, X, L, C, D and M.

Symbol       Value
I             1
V             5
X             10
L             50
C             100
D             500
M             1000
For example, 2 is written as II in Roman numeral, just two one's added together. 12 is written as XII, which is simply X + II. The number 27 is written as XXVII, which is XX + V + II.

Roman numerals are usually written largest to smallest from left to right. However, the numeral for four is not IIII. Instead, the number four is written as IV. Because the one is before the five we subtract it making four. The same principle applies to the number nine, which is written as IX. There are six instances where subtraction is used:

I can be placed before V (5) and X (10) to make 4 and 9. 
X can be placed before L (50) and C (100) to make 40 and 90. 
C can be placed before D (500) and M (1000) to make 400 and 900.
Given an integer, convert it to a roman numeral.



### Sample Input
```
num = 58
```
### Sample Output
```
"LVIII"
```

### Solution
```cpp
class Solution {
public:
    string intToRoman(int num) {
        vector<string>thousand_place={"","M","MM","MMM"};
        vector<string>hundred_place={"","C","CC","CCC","CD","D","DC","DCC","DCCC","CM"};
        vector<string>tens_place={"","X","XX","XXX","XL","L","LX","LXX","LXXX","XC"};
        vector<string>ones_place={"","I","II","III","IV","V","VI","VII","VIII","IX"};
        
        int t=num/1000;
        int h=(num%1000)/100;
        int te=(num%100)/10;
        int o=num%10;
        
        string ans=thousand_place[t]+hundred_place[h]+tens_place[te]+ones_place[o];
        return ans;
    }
};
```