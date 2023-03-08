# Merge k Sorted Lists &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/merge-k-sorted-lists/)

```
Linked List, Priority Queue
``` 
### Problem Statement 

You are given an array of k linked-lists lists, each linked-list is sorted in ascending order.

Merge all the linked-lists into one sorted linked-list and return it.

### Sample Input
```
lists = [[1,4,5],[1,3,4],[2,6]]
```
### Sample Output
```
[1,1,2,3,4,4,5,6]
```

### Solution
```cpp
class Solution {
public:
    ListNode* mergeKLists(vector<ListNode*>& lists) {
        int n=lists.size();
                                   priority_queue<pair<int,ListNode*>,vector<pair<int,ListNode*>>,greater<pair<int,ListNode*>>>pq;
        
        ListNode*ans=NULL;
        ListNode*temp=NULL;
        
        for(int i=0;i<n;i++){
            ListNode *l=lists[i];
            if(l!=NULL){              //to solve  [[]]
            int num=l->val;
            pq.push({num,l});
            }
        }
        
        while(!pq.empty()){
            ListNode*topNode=pq.top().second;
            pq.pop(); 
            
              ListNode*f=topNode->next;
              topNode->next=NULL;
            
             
              if(f!=NULL){
               pq.push({f->val,f});
              }
             
            if(ans==NULL){
                ans=topNode;
                temp=ans;
            }else{
                while(temp->next!=NULL){
                   temp=temp->next;
                }
                temp->next=topNode;
                temp=temp->next;
            }
               
        }
        
        return ans;
                                       
 }  
};
