
# Gas Station &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/gas-station/description/)

```
Array, Greedy
``` 
### Problem Statement 
There are n gas stations along a circular route, where the amount of gas at the ith station is gas[i].

You have a car with an unlimited gas tank and it costs cost[i] of gas to travel from the ith station to its next (i + 1)th station. You begin the journey with an empty tank at one of the gas stations.

Given two integer arrays gas and cost, return the starting gas station's index if you can travel around the circuit once in the clockwise direction, otherwise return -1. If there exists a solution, it is guaranteed to be unique

 
### Sample Input
```
gas = [1,2,3,4,5], cost = [3,4,5,1,2]
```
### Sample Output
```
3
```

### Solution
```cpp
class Solution {
public:
    int canCompleteCircuit(vector<int>& gas, vector<int>& cost) {
        //1st condition to go in circle is sum cost of all stations must be less than or equal to sum of gas of all stations.

        int total_gas=0;
        int total_cost=0;

        for(int i=0;i<gas.size();i++){
            total_gas+=gas[i];
            total_cost+=cost[i];
        }

        if(total_gas<total_cost) return -1;

       //At start gas is zero;
        int gasCurrently=0;

        //now that an unique solution exists, we will keep record of gasCurrently at each gas station.
        // At any station if it is negative it means all the gas stations before it can not be solution so we check for the next gas station as probable ans;

        int ans=0;

        for(int i=0;i<gas.size();i++){
            gasCurrently+=(gas[i]-cost[i]);
            if(gasCurrently<0){
                gasCurrently=0;
                ans=i+1;
            }
        }

        return ans;
        
    }
};
```