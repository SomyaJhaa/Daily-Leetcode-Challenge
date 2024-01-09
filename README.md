# Daily Leetcode Challenge Solutions

An attempt by me to apply my skills to help coding community.

## Always here to assist you guys.

## Today's 09-01-24 
## [872. Leaf-Similar Trees](https://leetcode.com/problems/leaf-similar-trees/description/?envType=daily-question&envId=2024-01-09)

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
The goal is to check whether the leaf values of two binary trees (root1 and root2) are similar. The leaf values should be compared in a left-to-right order. To achieve this, a depth-first search (DFS) approach is employed, utilizing stacks to traverse the trees.

# Approach
<!-- Describe your approach to solving the problem. -->
- Initialize two stacks s1 and s2 for the two trees.
- If either root1 or root2 is not null, push the corresponding root onto the stack.
- While both stacks are not empty, perform the following:
- - Compare the leaf value sequences using the dfs function.
- - If the sequences are not equal, return false.
- If both stacks become empty, return true (indicating leaf values are similar).
# DFS Function:

- The dfs function pops nodes from the stack and pushes their right and left children onto the stack.
- When a leaf node is encountered (both left and right children are null), return its value.
- This ensures that the leaf values are obtained in a left-to-right order.
# Edge Cases:

- Check if root1 and root2 are not null before pushing them onto the stacks.
# Summary:
The algorithm employs a stack-based DFS traversal to obtain leaf values in a left-to-right order for both trees. The leaf sequences are compared, and the function returns true if they are similar and false otherwise. The approach ensures efficient comparison of leaf values without explicitly constructing and comparing leaf value sequences.

# Complexity
- Time complexity: $O(N + M)$
- where N - number of nodes in root 1
- where M - number of nodes in root 2
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity:$O(max(N,M))$
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
    bool leafSimilar(TreeNode* root1, TreeNode* root2) {
        stack<TreeNode*> s1, s2;
        if(root1 != NULL)
        s1.push(root1);
        if(root2 != NULL) 
        s2.push(root2);
        while(!s1.empty() && !s2.empty())
            if(dfs(s1) != dfs(s2)) return false;
        return s1.empty() && s2.empty();    
    }
    int dfs(stack<TreeNode*>& s) {
        while(true) {
            TreeNode* node = s.top(); s.pop();
            if(node -> right) s.push(node->right);
            if(node -> left) s.push(node -> left);
            if(!node -> left && !node -> right) return node -> val;
        }
    }
};
```
