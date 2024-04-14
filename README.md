# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Always here to assist you guys.

## Today's 14-04-24

## [404. Sum of Left Leaves](https://leetcode.com/problems/sum-of-left-leaves/description/?envType=daily-question&envId=2024-04-14)

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
The goal is to find the sum of all left leaves in a binary tree. A left leaf is a leaf node that is the left child of its parent.
# Approach
<!-- Describe your approach to solving the problem. -->

- I started with the root node.
- If the current node is null, returned 0.
- Check if the left child of the current node exists and if it is a leaf node (i.e., it has no left or right children).
- If the left child is a leaf node, add its value to the result and continue recursively with the right child.
- If the left child is not a leaf node, recursively call the function on both the left and right children.
- Returned the sum obtained from the left subtree and the right subtree.

--- 
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)

# Complexity
- Time complexity : $O(n)$ 
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$n$ : number of nodes in the binary tree
- Space complexity : $O(n)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */

class Solution {
    public int sumOfLeftLeaves(TreeNode root) {
        if (root == null) {
            return 0;
        }
		
		// Checking if the left node is a leaf node
        if (root.left != null && root.left.left == null && root.left.right == null) {
            return root.left.val + sumOfLeftLeaves(root.right);
        }

		// Exploring the tree further
        return sumOfLeftLeaves(root.left) + sumOfLeftLeaves(root.right);
    }
}
```
