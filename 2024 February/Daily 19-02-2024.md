# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Always here to assist you guys.

## Today's 19-02-24 [Problem Link](https://leetcode.com/problems/power-of-two/description/?envType=daily-question&envId=2024-02-19)
## 231. Power of Two

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
The `isPowerOfTwo` method checks if a given number `n` is a power of two. If `n` is 1, it directly returns `true` as 1 is a power of two. Otherwise, I will call my helper method `recurse` to perform a recursive check.

# Approach
<!-- Describe your approach to solving the problem. -->
- Base Case : If `n` is equal to 1, returned `true` as 1 is a power of two.
- Recursive Case : If `n` is not 1, called my `recurse` method to handle the recursive check.
- My Helper Method (`recurse`) :
  - If `n` is 2, returned `true` as 2 is a power of two.
  - If `n` is less than 2 or not divisible by 2, returned `false` as it is not a power of two.
  - Recursively called the `recurse` method with `n/2`.

My approach utilized recursion to repeatedly check if the given number is divisible by 2 until reaching the base case of 2, which is a power of two.

---
Have a look at the code , still have any confusion then please let me know in the comments ... Keep Solving.:)

# Complexity
- Time complexity : $O(logn)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$n$ : given number
- Space complexity : $O(logn)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
    
    // Method to check if a number is a power of two
    public boolean isPowerOfTwo(int n) {
        // If n is 1, it is a power of two
        if (n == 1) {
            return true;
        }
        // Otherwise, checking recursively
        return recurse(n);
    }

    // Recursive method to check if a number is a power of two
    static boolean recurse(int n) {
        // If n is 2, it is a power of two
        if (n == 2) {
            return true;
        } else if (n < 2 || n % 2 != 0) {
            // If n is less than 2 or not divisible by 2, it is not a power of two
            return false;
        }
        // Recursively checking with n/2
        return recurse(n / 2);
    }
}
```