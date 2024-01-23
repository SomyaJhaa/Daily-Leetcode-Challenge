# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.


## Always here to assist you guys.

## Today's 23-01-24 [Problem Link](https://leetcode.com/problems/maximum-length-of-a-concatenated-string-with-unique-characters/description/?envType=daily-question&envId=2024-01-23)
## 1239. Maximum Length of a Concatenated String with Unique Characters


# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
As this problem aims to find the maximum length of a concatenated string with unique characters. To achieve this, I need to explore all possible combinations of strings and select those with unique characters. This involves using a bitmask approach to represent the set of characters present in a string efficiently.

# Approach
<!-- Describe your approach to solving the problem. -->
**Initialized a Data Structures :**
- Created an ArrayList `masks` to store the masks of valid strings (strings with unique characters).
   
**Generated Masks :**
- Iterated through the input strings (`arr`) and use the `getMask` function to obtain the mask for each string.
- Added valid masks to the `masks` ArrayList.

**Depth-First Search (DFS) :**
- Implemented the DFS function (`dfs`) to explore all possible combinations of masks and find the maximum length.
- Started DFS from index 0 with an initially empty set (`used`).

**DFS Exploration :**
- For each mask, checked if it can be added to the current combination (`used`).
- If yes, updated the result (`res`) with the maximum length obtained by adding the current mask.

**Result :**
- The final result is the count of set bits in the `used` mask, representing the maximum length of a concatenated string with unique characters.

**Helper Function (`getMask`) :**
- The `getMask` function converts a string into a bitmask, where each bit corresponds to a character's presence.
- Returns -1 if the string has duplicate characters, indicating it is not a valid mask.

---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)
# Complexity
- Time complexity : $O(2^n)$ 

$n$ : number of valid masks.
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity : $O(2^n)$ 
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
import java.util.ArrayList;
import java.util.List;

class Solution {

    // ArrayList to store the masks of valid strings
    static ArrayList<Integer> masks;

    public int maxLength(List<String> arr) {
        masks = new ArrayList<>();

        // Iterating through the input strings and get their masks, add valid masks to the ArrayList
        for (String s : arr) {
            int mask = getMask(s);
            if (mask != -1) {
                masks.add(mask);
            }
        }

        // Calling the DFS function starting from index 0 with an initially empty set
        return dfs(0, 0);
    }

    // DFS function to explore all possible combinations of masks
    static int dfs(int s, int used) {
        // Initialize the result with the count of set bits in the 'used' mask
        int res = Integer.bitCount(used);

        // Iterating through the masks and explore valid combinations
        for (int i = s; i < masks.size(); i++) {
            // Checking if the current mask can be added to the combination
            if ((used & masks.get(i)) == 0) {
                // Updating the result with the maximum length obtained by adding the current mask
                res = Math.max(res, dfs(i + 1, used | masks.get(i)));
            }
        }
        return res;
    }

    // Helper function to get the mask of a string, returns -1 if the string has duplicate characters
    static int getMask(String s) {
        int mask = 0;
        for (char c : s.toCharArray()) {
            int i = c - 'a';
            // Checking for duplicate characters in the string
            if ((mask & (1 << i)) != 0) {
                return -1;
            }
            // Set the corresponding bit for the character in the mask
            mask |= 1 << i;
        }
        return mask;
    }
}

```