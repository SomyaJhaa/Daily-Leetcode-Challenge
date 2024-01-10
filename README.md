# Daily Leetcode Challenge Solutions

An attempt by me to apply my skills to help coding community.

## Always here to assist you guys.

## Today's 10-01-24 
## [2385. Amount of Time for Binary Tree to Be Infected](https://leetcode.com/problems/amount-of-time-for-binary-tree-to-be-infected/description/?envType=daily-question&envId=2024-01-10)

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
My approach involves using a breadth-first search (BFS) algorithm to traverse the tree level by level, keeping track of the visited nodes. An unordered map is used to represent an adjacency list to store the relationships between nodes.

# Approach
<!-- Describe your approach to solving the problem. -->

1. **Initialization:**
   - Create an unordered map (`gr`) to represent an adjacency list, where each node is associated with its neighboring nodes.
   - Define a helper function `convert` to build the adjacency list.

2. **BFS Traversal:**
   - Start BFS from the given node (`start`) by using a queue (`q`) to store nodes at each level.
   - Initialize the `minute` variable to 0, representing the time taken to reach nodes.
   - Use a set (`visited`) to keep track of visited nodes and avoid revisiting them.

3. **BFS Loop:**
   - While the queue is not empty, dequeue nodes from the front and process them.
   - For each dequeued node, enqueue its neighboring nodes into the queue if they haven't been visited yet.
   - Mark the dequeued node as visited.

4. **Counting Levels:**
   - After processing all nodes at a level, increment the `minute` variable to represent the time taken to reach that level.
   - Continue the BFS until all nodes are visited.

5. **Result:**
   - The result is the `minute` variable minus 1, which represents the amount of time it takes to reach all nodes.
 
# Complexity
- Time complexity: $$O(n)$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: $$O(n)$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    int amountOfTime(TreeNode* root, int start) {
        unordered_map<int, vector<int>> gr;
        convert(root, 0, gr);
        queue<int> q;
        q.push(start);
        int minute = 0;
        unordered_set<int> visited;
        visited.insert(start);

        while(!q.empty()) {
            int sz = q.size();
            while(sz--) {
                int node = q.front();
                q.pop();

                for(int child : gr[node]) {
                    if(visited.find(child) == visited.end()) {
                        visited.insert(child);
                        q.push(child);
                    }
                }
            }
            minute++;
        }
        return minute - 1;
    }
    void convert(TreeNode* node, int parent, unordered_map<int, vector<int>>& gr) {
        if (node == nullptr) return;

        vector<int>& adjacentList = gr[node -> val];
        if (parent != 0) adjacentList.push_back(parent);
        if(node -> left != nullptr) adjacentList.push_back(node->left -> val);
         if(node -> right != nullptr) adjacentList.push_back(node->right -> val);

         convert(node -> left , node -> val, gr);
         convert(node -> right , node -> val, gr);
    }
};
```
