
# Clone Graph &ensp;  [![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/clone-graph/)

```
Graph, Hash Table, BFS
``` 
### Problem Statement 
Given a reference of a node in a connected undirected graph.

Return a deep copy (clone) of the graph.

Each node in the graph contains a value (int) and a list (List[Node]) of its neighbors.

class Node {
    public int val;
    public List<Node> neighbors;
}
 

Test case format:

For simplicity, each node's value is the same as the node's index (1-indexed). For example, the first node with val == 1, the second node with val == 2, and so on. The graph is represented in the test case using an adjacency list.

An adjacency list is a collection of unordered lists used to represent a finite graph. Each list describes the set of neighbors of a node in the graph.

The given node will always be the first node with val = 1. You must return the copy of the given node as a reference to the cloned graph.

### Sample Input
```
adjList = [[2,4],[1,3],[2,4],[1,3]]
```
### Sample Output
```
[[2,4],[1,3],[2,4],[1,3]]
```

### Solution
```cpp
class Solution {
public:
    Node* cloneGraph(Node* node) {
      if(node==NULL) return NULL;
        
      
      unordered_map<Node*,Node*>visited ; // All the catch is here
        
      queue<Node*>q;
      q.push(node);
      Node*ans=new Node(node->val);   //clone head node
      visited[node]=ans;
        
      while(q.size()){
          Node*parNode=q.front();
          q.pop();
              
          for(auto nbr:parNode->neighbors){
              if(visited.find(nbr)==visited.end()){
                  Node*n=new Node(nbr->val);
                  visited[nbr]=n;
                  q.push(nbr);  
              } 
              
              // whether newly made aur previously made you have to push them to the neighbors of current node if they are its neighbor
               visited[parNode]->neighbors.push_back(visited[nbr]); 
             
          }
      }
        
        return ans;
    }
};
```