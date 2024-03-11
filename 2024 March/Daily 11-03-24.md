# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Always here to assist you guys.

## Today's 11-03-24 
## [791. Custom Sort String](https://leetcode.com/problems/custom-sort-string/description/?envType=daily-question&envId=2024-03-11)

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
My given code implements a custom sort string function using a HashSet and a HashMap.

# Approach
<!-- Describe your approach to solving the problem. -->
**Initialization :**
   - Created a HashSet `h` to store characters in the given order.
   - Created a HashMap `m` to store characters and their counts in the input string.
   - Initialized an empty string `jawab` to store the final result.

**Processed Order Characters :**
   - Iterated through each character in the given order.
   - If the character is present in the input string (`m.containsKey(c)`), appended it to the result string `jawab` based on its count.

**Processed Remaining Characters :**
   - Iterated through each character in the input string.
   - If the character is not in the given order (`!h.contains(c)`), added it to the order, and append it to the result string `jawab` based on its count.

**Result :**
   - The final result string `jawab` contained the custom-sorted string based on the given order.

My approach ensured that the characters are processed according to the specified order, and the resulting string follows the custom sorting criteria.

---
Have a look at the code , still have any confusion then please let me know in the comments ... Keep Solving.:)

# Complexity
- Time complexity : $O( O + S + N )$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$O$ : length of the order string

$S$ : length of the input string

$N$ :  total number of characters in the input string
- Space complexity : $O( O + S + N )$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
// This is a Java implementation of a custom sort string function.
// I used a HashSet and a HashMap to process the order and input string.

class Solution {

    // HashSet to store characters in the given order
    static HashSet<Character> h;
    // HashMap to store characters and their counts in the input string
    static HashMap<Character, Integer> m;
    // String to store the final result
    static String jawab;

    // Function to custom sort the input string based on the given order
    public String customSortString(String order, String s) {
        // Initializing the HashSet with the order characters
        h = new HashSet<>();
        for (char c : order.toCharArray()) {
            h.add(c);
        }

        // Initializing the HashMap with characters and their counts in the input string
        m = new HashMap<>();
        for (char c : s.toCharArray()) {
            m.put(c, m.getOrDefault(c, 0) + 1);
        }

        // Initializing the result string
        jawab = "";

        // Processing characters in the given order and append them to the result string
        for (char c : order.toCharArray()) {
            if (m.containsKey(c)) {
                for (int i = 0; i < m.get(c); i++) {
                    jawab += c;
                }
            }
        }

        // Processing remaining characters in the input string and append them to the result string
        for (char c : s.toCharArray()) {
            if (!h.contains(c)) {
                h.add(c);
                for (int i = 0; i < m.get(c); i++) {
                    jawab += c;
                }
            }
        }

        // Returning the final result string
        return jawab;
    }
}
```
