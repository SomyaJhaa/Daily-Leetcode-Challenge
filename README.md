# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Always here to assist you guys.

## Today's 07-04-24 

## [678. Valid Parenthesis String](https://leetcode.com/problems/valid-parenthesis-string/description/?envType=daily-question&envId=2024-04-07)

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
My algorithm aims to determine whether a given string containing parentheses, '*' (wildcards), and other characters forms a valid combination of parentheses. In a valid combination, each open parenthesis '(' must have a corresponding closing parenthesis ')', and wildcards '*' can be either an open parenthesis, a closing parenthesis, or an empty string. 

# Approach
<!-- Describe your approach to solving the problem. -->

- I iterated through each character in the string and maintain two counts :
  - `minOpen`: Represents the minimum count of open parentheses that must be closed.
  - `maxOpen`: Represents the maximum count of open parentheses that could be closed.

- I traversed the string character by character:
  - If I encountered an open parenthesis '(', both `minOpen` and `maxOpen` are incremented.
  - If I encountered a closing parenthesis ')', I decrement `minOpen` (ensuring it doesn't go below 0) and decrement `maxOpen`.
  - If I encountered a wildcard '*', I decrement `minOpen` (ensuring it doesn't go below 0) and increment `maxOpen` because it can act as an open parenthesis, closing parenthesis, or an empty string.

- At any point during the iteration, if the count of open parentheses (`maxOpen`) became negative, it means I have encountered more closing parentheses than open ones, which makes the string invalid, so I return `false`.

- Finally, I checked if all open parentheses are closed by verifying if `minOpen` is back to 0. If it is, then the string is valid; otherwise, it's invalid.

- My algorithm returned `true` if the string is valid and `false` otherwise.

--- 
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)

# Complexity
- Time complexity : $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$n$ :  length of the input string
- Space complexity : $O(1)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
  public boolean checkValidString(String str) {
    
    // Initializing the minimum and maximum counts of open parentheses
    int minOpen = 0;  // minimum count of open parentheses
    int maxOpen = 0;  // maximum count of open parentheses

    // Iterating through each character in the string
    for (char ch : str.toCharArray()) {
        // Handling different cases based on the character
        switch (ch) {
            
            case '(':
                // Incrementing both minimum and maximum counts for open parentheses
                minOpen++;
                maxOpen++;
                break;
            case ')':
                // Decreasing the minimum count, but ensure it doesn't go negative
                minOpen = Math.max(0, --minOpen);
                // Decreasing the maximum count for open parentheses
                maxOpen--;
                break;
            case '*':
                // Decreasing the minimum count, but ensure it doesn't go negative
                minOpen = Math.max(0, --minOpen);
                // Incrementing the maximum count for open parentheses
                maxOpen++;
                break;
        }
        
        // If the maximum count of open parentheses becomes negative, return false
        if (maxOpen < 0){
            return false;
        }
    }

    // Checking if all open parentheses are closed
    return minOpen == 0;
  }
}
```
