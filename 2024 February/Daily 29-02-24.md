# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Always here to assist you guys.

## Today's 29-02-24 [Problem Link](https://leetcode.com/problems/even-odd-tree/description/?envType=daily-question&envId=2024-02-29)
## 1609. Even Odd Tree

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
The problem requires determining whether a binary tree is an "Even-Odd Tree." An Even-Odd Tree is a binary tree where :

- The values at each level alternate between odd and even.
- For each level, the values are strictly increasing from left to right.

The task is to check if the given binary tree adheres to these conditions.

# Approach
<!-- Describe your approach to solving the problem. -->
To solve this problem, I can use a level-order traversal (breadth-first search) of the binary tree. I will maintain a queue to process nodes level by level. At each level, I just need to check if the conditions for an Even-Odd Tree are satisfied.

**Initialize the queue and level flag :** I started by adding the root node to the queue and set the initial level flag to even.

**Level-Order Traversal :** Used a loop to process each level of the tree. Inside the loop:
   - Checked if the current level is valid using a helper function.
   - Toggled the level flag (odd to even or even to odd) for the next level.
   - Continued until the queue is empty.

**Helper Function (isValidLevel) :** This function is responsible for checking if the current level adheres to the Even-Odd Tree conditions. It performed the following steps :
   - Initialized the previous value based on whether the level is odd or even.
   - Iterated through the nodes at the current level.
   - Checked if the values violate the conditions (e.g., odd values on even levels, even values on odd levels).
   - Updated the previous value for the next iteration.
   - Enqueued the left and right children if they exist.

**Result :** If all levels passed the validation, returned true, indicating that the binary tree is an Even-Odd Tree; otherwise, returned false.

My approach ensured a systematic examination of each level, verifying the required conditions at each step.

---
Have a look at the code , still have any confusion then please let me know in the comments ... Keep Solving.:)v
# Complexity
- Time complexity : $O(N)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$N$ : number of nodes in the binary tree
- Space complexity :  $O(N/2)$ ${\equiv}$ $O(N)$
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

    // Global queue to perform level-order traversal
    static Queue<TreeNode> q;
    
    // Flag to keep track of odd or even level
    static boolean oddlevel;
    
    public boolean isEvenOddTree(TreeNode root) {
        // Checking if the root is null
        if (root == null) {
            return false;
        }

        // Initializing the queue with the root
        q = new LinkedList<>();
        q.offer(root);

        // Starting with even level
        oddlevel = false;

        // Performing level-order traversal
        while (!q.isEmpty()) {
            // Checking if the level is valid
            if (!isValidLevel()) {
                return false;
            }

            // Toggle to the next level
            oddlevel = !oddlevel;
        }

        // If all levels are valid, returning true
        return true;
    }

    // Helper function to check if the current level is valid
    static boolean isValidLevel() {
        // Initialize the previous value based on odd or even level
        int prevValue = oddlevel ? Integer.MAX_VALUE : Integer.MIN_VALUE;

        // Iterating through the current level
        for (int s = q.size(); s > 0; s--) {
            // Polling the front of the queue
            TreeNode t = q.poll();

            // Checking if the value violates the conditions based on odd or even level
            if (oddlevel && (t.val % 2 != 0 || t.val >= prevValue)) {
                return false;
            }
            if (!oddlevel && (t.val % 2 == 0 || t.val <= prevValue)) {
                return false;
            }

            // Updating the previous value
            prevValue = t.val;

            // Enqueuing the left and right children if they exist
            if (t.left != null) {
                q.offer(t.left);
            }
            if (t.right != null) {
                q.offer(t.right);
            }
        }

        // The level is valid
        return true;
    }
}
```