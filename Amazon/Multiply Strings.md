# Multiply Strings   [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/multiply-strings/)

```
Strings, Math
```
### Problem Statement 
Given two non-negative integers num1 and num2 represented as strings, return the product of num1 and num2, also represented as a string.

Note: You must not use any built-in BigInteger library or convert the inputs to integer directly.

### Sample Input
```
num1 = "123", num2 = "456"
```
### Sample Output
```
"56088"
```

### Solution
```cpp
class Solution {
public:
     // simple multiplication digit by digit and then adding the results.

    string addString(string a,string b){
        string ans="";
        int l1=a.size(),l2=b.size();
        int rem=0;
        int i=l2-1,j=l1-1;
        while(i>=0){
            int sum=(b[i]-'0')+(a[j]-'0')+rem;
            ans.push_back(sum%10+'0');
            rem=sum/10;
            i--;
            j--;
        }
        
        while(j>=0){
            int sum=(a[j]-'0')+rem;
            ans.push_back(sum%10+'0');
            rem=sum/10;
            j--;
        }

        while(rem){
            ans.push_back(rem%10+'0');
            rem=rem/10;
        }

        reverse(ans.begin(),ans.end());
        return ans;
        
    }

    string multiply(string num1, string num2) {
        if(num1=="0" || num2=="0") return "0";
        string  res="";
        int counter=0;

        for(int i=num2.size()-1;i>=0;i--){
            int n1=num2[i]-'0';
            int rem=0;
            string temp=""; 

            for(int count=1;count<=counter;count++) temp.push_back('0');

            for(int j=num1.size()-1;j>=0;j--){
                int n2=num1[j]-'0';
                int resNum=n1*n2+rem;
                int resNum1=resNum%10;
                rem=resNum/10;

                temp.push_back(resNum1+'0');
            }
            while(rem){
                 temp.push_back(rem%10+'0');
                 rem/=10;
            }
            reverse(temp.begin(),temp.end());
           
            if(res==""){
                res=temp;
            }else{
                res=addString(temp,res);
            }
            temp="";
            counter++;
        }

        return res;
    }
};
`