# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Always here to assist you guys.

## Today's 01-03-24 [Problem Link](https://leetcode.com/problems/maximum-odd-binary-number/description/?envType=daily-question&envId=2024-03-01)
## 2864. Maximum Odd Binary Number

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
The goal of the code is to find the maximum odd binary number based on the input binary string `s`. The approach involves counting the number of '1's in the input string and constructing a new binary string accordingly.


# Approach
<!-- Describe your approach to solving the problem. -->

**Counted '1's :**
   - Initialized a static variable `ones` to count the number of '1's.
   - Iterated through each character in the input string `s`.
   - If the character is '1', incremented the `ones` count.

**Constructed the Result String  :**
   - Initialized an empty string `jawab` to store the result.
   - Added ('1's - 1) times '1' to the result string.
   - Added ('0's - 1) times '0' to the result string.
   - If there is at least one '1' in the input string, added a final '1' to the result.

**Result :**
   - The constructed string `jawab` represents the maximum odd binary number.
   - Returned the result string.

My code ensures that the resulting binary number is odd by including a final '1' in the string. The approach efficiently constructs the result based on the count of '1's in the input string.

---
Have a look at the code , still have any confusion then please let me know in the comments ... Keep Solving.:)
# Complexity
- Time complexity : $O(s)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$s$ : length of the input string
- Space complexity : $O(s)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
    
    // Static variable to count the number of '1's in the input string
    static int ones;

    // Method to find the maximum odd binary number
    public String maximumOddBinaryNumber(String s) {
        
        // Initializing the count of '1's
        ones = 0;

        // Counting the number of '1's in the input string
        for (char c : s.toCharArray()) {
            if (c == '1') {
                ones++;
            }
        }

        // Initializing an empty string to store the result
        String jawab = "";

        // Adding '1's to the result string (ones - 1) times
        for (int i = 0; i < ones - 1; i++) {
            jawab += '1';
        }

        // Adding '0's to the result string (s.length() - ones) times
        for (int i = 0; i < s.length() - ones; i++) {
            jawab += '0';
        }

        // If there is at least one '1' in the input string, adding a final '1'
        if (ones > 0) {
            jawab += '1';
        }

        // Returning the result string
        return jawab;
    }
}
```
