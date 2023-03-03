# LRU Cache

### Problem Statement 

[![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/lru-cache/)

Design a data structure that follows the constraints of a Least Recently Used (LRU) cache.

Implement the LRUCache class:

LRUCache(int capacity) Initialize the LRU cache with positive size capacity.
int get(int key) Return the value of the key if the key exists, otherwise return -1.
void put(int key, int value) Update the value of the key if the key exists. Otherwise, add the key-value pair to the cache. If the number of keys exceeds the capacity from this operation, evict the least recently used key.
The functions get and put must each run in O(1) average time complexity.

### Sample Input
```
["LRUCache", "put", "put", "get", "put", "get", "put", "get", "get", "get"]
[[2], [1, 1], [2, 2], [1], [3, 3], [2], [4, 4], [1], [3], [4]]
```
### Sample Output
```
[null, null, null, 1, null, -1, null, -1, 3, 4]
```

### Solution
```cpp
class LRUCache {  
public:

class node{
   public:
   int key;
   int val;
   node* prev=NULL;
   node* next=NULL;
   node(int k , int v){
       key=k;
       val=v;
   }
};

   int capacity;
   unordered_map<int,node*>mp;

   node*head=new node(-1,-1);
   node*tail=new node(-1,-1);

   void deleteNode(node* n){
         n->prev->next=n->next;
         n->next->prev=n->prev;
         n->next=NULL;
         n->prev=NULL;
      }

      void insertNode(node* n){
           node* tempNext=head->next;
           head->next=n;
           n->prev=head;
           n->next=tempNext;
           n->next->prev=n;
       }

    LRUCache(int capacity) {
        this->capacity=capacity;
        head->next=tail;
        tail->prev=head;
    }
    
    int get(int key) {
        if(mp.find(key)!=mp.end()) {
            node* resNode= mp[key];
            //delete it from linked list and make a new node and insert it just after head
            mp.erase(key);
            deleteNode(resNode);
            insertNode(resNode);
            mp[key]=head->next;
            return resNode->val;
        }
        return -1; 
    }
    
    void put(int key, int value) {
         if(mp.find(key)!=mp.end()){
             //delete the node 
            node* n=mp[key];
            mp.erase(key);
            deleteNode(n);

         }else{
             if(mp.size()==capacity){
                 //delete the node just before tail
                 mp.erase(tail->prev->key);
                 deleteNode(tail->prev);
             }
         }
         //insert the new node just after head
         node* newNode=new node(key,value);
         insertNode(newNode);
         mp[key]=head->next;
        
    }
};
`