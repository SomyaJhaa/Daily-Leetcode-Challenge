# Celebrating Unity in Diversity: Happy Republic Day ! :india:


# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.


## Always here to assist you guys.

<<<<<<< HEAD
## Today's 26-01-24 [Problem Link](https://leetcode.com/problems/out-of-boundary-paths/description/?envType=daily-question&envId=2024-01-26)
## 576. Out of Boundary Paths
=======
## Today's 25-01-24 
## [1143. Longest Common Subsequence](https://leetcode.com/problems/longest-common-subsequence/description/?envType=daily-question&envId=2024-01-25)
>>>>>>> e8399d5c5e247fcb22a7717e733ce019db11296b


# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
<<<<<<< HEAD
This problem involves finding the number of paths a ball can take to move out of a grid within a given number of moves. My goal is to optimize the solution using dynamic programming to avoid redundant calculations.

# Approach
<!-- Describe your approach to solving the problem. -->
I have utilized dynamic programming approach with memoization to efficiently calculate the number of paths. A recursive helper function is defined to explore all possible moves, and a 3D memoization array is used to store and retrieve previously computed results.

#### Recursive Helper Function

My recursive function is responsible for calculating the number of paths from a given cell with a specified number of remaining moves. Key points of the recursive function include:
- Base cases : Handled scenarios where the ball moves outside the grid or runs out of moves.
- Memoization : Stored and retrieved results using a 3D array to avoid redundant calculations.
- Recursive step : Explored all possible moves (up, down, left, right) and sum up the results with modulo to prevent integer overflow.

#### Code Explanation
My Java code provided implements the described approach. The `findPaths` function initializes the memoization array and calls the recursive helper function. The `helper` function handles the recursive calculations and memoization.
=======
This problem aims to find the length of the longest common subsequence (LCS) between two given strings, `text1` and `text2`. A subsequence is a sequence that appears in the same relative order, but not necessarily contiguous. The code uses dynamic programming to efficiently find the length of the LCS.

# Approach
<!-- Describe your approach to solving the problem. -->
**Dynamic Programming Array (dp) :**
   - Created a 2D array `dp` of dimensions `(1 + text1.length()) x (1 + text2.length())` to store the lengths of common subsequences for different prefixes of the input strings.
   - `dp[i][j]` represents the length of the LCS for the prefixes of `text1` up to index `i-1` and `text2` up to index `j-1`.

**Nested Loop Iteration :**
   - Iterated through each character in `text1` (using index `i`).
   - For each character in `text1`, iterated through each character in `text2` (using index `j`).
   
**Character Comparison :**
   - If the characters at the current positions (i, j) in both strings are equal:
      - Incremented the length of the common subsequence by 1: `dp[i + 1][j + 1] = 1 + dp[i][j]`.
   - If the characters are not equal:
      - Choosed the maximum length from the previous positions:
        `dp[i + 1][j + 1] = Math.max(dp[i + 1][j], dp[i][j + 1])`.

**Result :**
   - The value at the bottom-right corner of the array (`dp[text1.length()][text2.length()]`) contains the length of the longest common subsequence.

**Return :**
   - Returned the length of the LCS as the final result.

My dynamic programming approach efficiently breaks down the problem into subproblems, avoiding redundant computations and providing an optimal solution for finding the length of the longest common subsequence.
>>>>>>> e8399d5c5e247fcb22a7717e733ce019db11296b

---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)

# Complexity
<<<<<<< HEAD
- Time complexity : $O(m * n * maxMove)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$m$ :  number of rows in the grid
$n$ :  number of columns in the grid
$maxMove$ :  maximum number of moves allowed
- Space complexity :  $O(m * n * (1+maxMove))$ ~  $O(m * n * maxMove)$
=======
- Time complexity : $O(a*b)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$a$ : length of string 'text1'

$b$ : length of string 'text2'
- Space complexity : $O(a*b)$
>>>>>>> e8399d5c5e247fcb22a7717e733ce019db11296b
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
    
    public int longestCommonSubsequence(String text1, String text2) {
        
        // Creating a 2D array to store the length of common subsequences
        int[][] dp = new int[1 + text1.length()][1 + text2.length()];

<<<<<<< HEAD
    // Modulo value for the result
    static int mod = 1_000_000_007;

    // Main function to find paths
    public int findPaths(int m, int n, int maxMove, int startRow, int startColumn) {
        
        // Creating 3D array to store previously calculated results
        Integer[][][] h = new Integer[1 + maxMove][m][n];
        return helper(startRow, startColumn, maxMove, m, n, h);
    }

    // Helper function for recursive calculations
    static int helper(int r, int c, int max, int m, int n, Integer[][][] h) {
        // Base case: if the cell is outside the grid, count it as a path
        if (r < 0 || c < 0 || r == m || c == n) {
            return 1;
        }
        
        // Base case: if the maximum moves are exhausted, no more paths
        if (max == 0) {
            return 0;
        }

        // If the result for the current state is already calculated, returning it
        if (h[max][r][c] != null) {
            return h[max][r][c];
        }

        // Recursively calculating of paths by moving in all possible directions
        h[max][r][c] = (int) ((
                (helper(r, c + 1, max - 1, m, n, h)) * 1L +
                helper(r, c - 1, max - 1, m, n, h) +
                helper(r + 1, c, max - 1, m, n, h) +
                helper(r - 1, c, max - 1, m, n, h)
        ) % mod);

        // Storing the calculated result and return it
        return h[max][r][c];
=======
        // Iterating through each character in text1
        for (int i = 0; i < text1.length(); i++) {
            // Iterating through each character in text2
            for (int j = 0; j < text2.length(); j++) {
                // Checking if the characters at the current positions are equal
                if (text1.charAt(i) == text2.charAt(j)) {
                    // If equal, extending the common subsequence length by 1
                    dp[i + 1][j + 1] = 1 + dp[i][j];
                } else {
                    // If not equal, choosing the maximum length from the previous positions
                    dp[i + 1][j + 1] = Math.max(dp[i + 1][j], dp[i][j + 1]);
                }
            }
        }

        // The value at the bottom-right corner of the array contains the length of the longest common subsequence
        return dp[text1.length()][text2.length()];
>>>>>>> e8399d5c5e247fcb22a7717e733ce019db11296b
    }
}

```
