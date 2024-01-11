# Daily Leetcode Challenge Solutions

An attempt by me to apply my skills to help coding community.

## Always here to assist you guys.

## Today's 11-01-24 
## [1026. Maximum Difference Between Node and Ancestor](https://leetcode.com/problems/maximum-difference-between-node-and-ancestor/description/?envType=daily-question&envId=2024-01-11)


# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
To find the maximum absolute difference between the values of any ancestor and its descendant, we need to explore the entire binary tree. We can achieve this by performing a depth-first search (DFS) on the tree. During the traversal, we need to keep track of the minimum and maximum values encountered in the path from the root to the current node.

# Approach
<!-- Describe your approach to solving the problem. -->
1. We define a recursive function `maxD` that takes a node, the maximum value encountered so far (`maxV`), and the minimum value encountered so far (`minVal`).
2. In the `maxD` function, if the current node is `nullptr`, we return the difference between the maximum and minimum values encountered in the path (`maxV - minVal`).
3. Otherwise, we update `maxV` and `minVal` based on the current node's value.
4. We then recursively call `maxD` for the left and right children of the current node, passing the updated `maxV` and `minVal`.
5. The final result is the maximum of the results obtained from the left and right subtrees.

The `maxAncestorDiff` function initializes the process with the root node by calling `maxD(root, root->val, root->val)`.

**Example:**
Consider the given example with the root values `[8,3,10,1,6,null,14,null,null,4,7,13]`. The DFS traversal may look like this:

- Starting with root (8), `maxD(8, 8, 8)`
  - Left child (3): `maxD(3, 8, 3)`
    - Left child (1): `maxD(1, 8, 1)` (update maxV to 8, minVal to 1)
    - Right child (6): `maxD(6, 8, 1)` (update maxV to 8, minVal to 1)
      - Left child (4): `maxD(4, 8, 1)` (update maxV to 8, minVal to 1)
      - Right child (7): `maxD(7, 8, 1)` (update maxV to 8, minVal to 1)
  - Right child (10): `maxD(10, 10, 3)`
    - Right child (14): `maxD(14, 14, 3)`
      - Left child (13): `maxD(13, 14, 3)` (update maxV to 14, minVal to 3) 


# Complexity
- Time complexity: $O(n)$
- n = number of nodes
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: $O(h)$
- h = height of the tree
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
    int maxDiff(TreeNode* node, int maxVal, int minVal) {
        if(node == nullptr) return maxVal - minVal;

        maxVal = max(maxVal, node -> val);
        minVal = min(minVal, node -> val);

        int maxLeftDiff = maxDiff(node-> left, maxVal, minVal);
        int maxRightDiff = maxDiff(node-> right, maxVal, minVal);

        return max(maxLeftDiff, maxRightDiff);
    }
    
    int maxAncestorDiff(TreeNode* root) {
        if(root == nullptr) return 0;
        return maxDiff(root, root -> val, root -> val);
        
    }
};
```