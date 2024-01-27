
# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.


## Always here to assist you guys.

## Today's 27-01-24 
## [629. K Inverse Pairs Array](https://leetcode.com/problems/k-inverse-pairs-array/description/?envType=daily-question&envId=2024-01-27)

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
This problem requires counting the number of permutations of numbers from 1 to n with a given number of inverse pairs. An inverse pair in a permutation (a[i], a[j]) is defined as (i < j and a[i] > a[j]). The goal is to find the count of permutations with a specific number of inverse pairs.


# Approach
<!-- Describe your approach to solving the problem. -->
**Base Case :** 
  - When j is 0 (no inverse pairs), there is only one way to arrange the numbers, i.e., the ascending order. So, dp[i][0] is set to 1 for all i.

**Dynamic Programming Transition :**
   - For each i and j, I updated the dp[i][j] using the following recurrence relation:
     ```
     dp[i][j] = (dp[i][j - 1] + dp[i - 1][j]) % MOD;
     ```
     This accounted for permutations with the same number of inverse pairs as the previous step.
   
   - Additionally, if (j - i) is non-negative, I subtracted the count of permutations with (j - i) inverse pairs to avoid double counting:
     ```
     dp[i][j] = (dp[i][j] - dp[i - 1][j - i] + MOD) % MOD;
     ```

**Result :**
   - The final result is stored in `dp[n][k]`, representing the count of permutations of numbers 1 to n with k inverse pairs.

---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)


# Complexity
- Time complexity : $O(n*k)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity : $O(n*k)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
    static int MOD = 1_000_000_007;

    // Function to calculate the number of arrays with k inverse pairs
    public int kInversePairs(int n, int k) {
        // gp[i][j] representing the number of arrays of length i with j inverse pairs
        int[][] gp = new int[n + 1][k + 1];

        // Base case: If there are no inverse pairs (j=0), there is only one array (empty array).
        for (int i = 0; i <= n; i++) {
            gp[i][0] = 1;
        }

        // Dynamic Programming to fill the gp array
        for (int i = 1; i <= n; ++i) {
            for (int j = 1; j <= k; ++j) {
                // Calculating the number of arrays with j inverse pairs
                gp[i][j] = (gp[i][j - 1] + gp[i - 1][j]) % MOD;
                
                // If j - i is non-negative, subtracting the count of arrays with (j - i) inverse pairs
                if (j - i >= 0) {
                    gp[i][j] = (gp[i][j] - gp[i - 1][j - i] + MOD) % MOD;
                }
            }
        }

        // Returning the result, which represents the number of arrays of length n with k inverse pairs
        return gp[n][k];
    }
}

```
