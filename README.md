# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Always here to assist you guys.

## Today's 06-04-24 

## [1249. Minimum Remove to Make Valid Parentheses](https://leetcode.com/problems/minimum-remove-to-make-valid-parentheses/description/?envType=daily-question&envId=2024-04-06)

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
To address this problem, I utilize a stack to manage the indices of unpaired '(' characters. I traverse the string, marking unpaired ')' characters as '#' and popping indices from the stack for each encountered ')', effectively pairing '(' and ')'. Any remaining unpaired '(' characters are marked as '#' after processing. Finally, I remove all '#' characters to obtain the valid string.

# Approach
<!-- Describe your approach to solving the problem. -->
**Initialized** an empty stack (`parenthesesStack`) to store indices of unpaired '(' characters.

**Traversed** the input string character by character:
   - If the current character is '(', push its index onto `parenthesesStack`.
   - If the current character is ')':
     - If `parenthesesStack` is empty, marked the ')' character as '#'.
     - If `parenthesesStack` is not empty, popped the top index to pair '(' and ')'.

**Marked** any remaining unpaired '(' characters as '#' by popping from `parenthesesStack`.

**Removed** all '#' characters from the modified string.

**Returned** the resulting string, which now contains the minimum removed parentheses to make it valid.

--- 
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)

# Complexity
- Time complexity : $O(s)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$s$ :  length of the input string
- Space complexity : $O(s)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
    public String minRemoveToMakeValid(String s) {

        Deque<Integer> parenthesesStack = new ArrayDeque<>(); // Stores indices of unpaired '(' characters
        StringBuilder modifiedString = new StringBuilder(s);

        for (int i = 0; i < s.length(); ++i) {
            if (modifiedString.charAt(i) == '(') {
                parenthesesStack.push(i); // Record the unpaired '(' index.
            } 
            else if (modifiedString.charAt(i) == ')') {
                if (parenthesesStack.isEmpty()) {
                    modifiedString.setCharAt(i, '#'); // Mark the unpaired ')' as '#'.
                } 
                else {
                    parenthesesStack.pop(); // Find a pair!
                }
            }
        }

        // Marking the unpaired '(' as '#'.
        while (!parenthesesStack.isEmpty()) {
            modifiedString.setCharAt(parenthesesStack.pop(), '#');
        }

        return modifiedString.toString().replaceAll("#", "");
    }
}

```
