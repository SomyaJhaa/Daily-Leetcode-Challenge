# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Always here to assist you guys.

## Today's 02-04-24 

## [205. Isomorphic Strings](https://leetcode.com/problems/isomorphic-strings/description/?envType=daily-question&envId=2024-04-02)

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
To check if two strings are isomorphic, we need to establish a one-to-one mapping between characters in one string to characters in the other string. This mapping must preserve the order of characters and ensure that no two characters map to the same character, while allowing a character to map to itself.

# Approach
<!-- Describe your approach to solving the problem. -->
**Initialization** : Initialized two hash maps (`sToTMap` and `tToSMap`) to store mappings from characters in string `s` to characters in string `t`, and vice versa.
   
**Iteration** : Iterated through each character in the strings `s` and `t`.
   
**Mapping Check** :
   - For each character pair `(sChar, tChar)`, checked if `sChar` is already mapped to a character in `t` and if `tChar` is already mapped to a character in `s`.
   - If a mapping existed and the mapped characters are not equal to each other, returned `false`.
   - If a mapping does not exist, established the mapping by adding the characters to their respective maps.

**Completion** : If the loop completes without returning `false`, returned `true`, indicating that the strings are isomorphic.

--- 
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)
# Complexity
- Time complexity : $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$n$ : length of the strings `s` and `t` 
- Space complexity : $O(min(m, n))$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
$m$ : size of the character set 

# Code
```
class Solution {
    public boolean isIsomorphic(String s, String t) {

        // Initializing two hash maps to store mappings
        Map<Character, Character> sToTMap = new HashMap<>();
        Map<Character, Character> tToSMap = new HashMap<>();
        
        // Iterating through each character in the strings s and t
        for (int i = 0; i < s.length(); i++) {
            char sChar = s.charAt(i);
            char tChar = t.charAt(i);
            
            // Checking if sChar is already mapped to a character in t
            if (sToTMap.containsKey(sChar)) {
                // If the mapped character is not equal to tChar, returning false
                if (sToTMap.get(sChar) != tChar) {
                    return false;
                }
            } else {
                // If sChar is not mapped, mapping it to tChar
                sToTMap.put(sChar, tChar);
            }
            
            // Checking if tChar is already mapped to a character in s
            if (tToSMap.containsKey(tChar)) {
                // If the mapped character is not equal to sChar, returning false
                if (tToSMap.get(tChar) != sChar) {
                    return false;
                }
            } else {
                // If tChar is not mapped, mapping it to sChar
                tToSMap.put(tChar, sChar);
            }
        }
        
        // If the loop completes without returning false, returning true
        return true;
    }
}
```
