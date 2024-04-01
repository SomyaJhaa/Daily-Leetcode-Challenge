# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Always here to assist you guys.

## Today's 01-04-24 

## [58. Length of Last Word](https://leetcode.com/problems/length-of-last-word/?envType=daily-question&envId=2024-04-01)


**Intuition:**
The code aims to find the length of the last word in a given string `s`. It iterates through the string from the end, counting the characters until a space is encountered. Once a space is found, it returns the count if it's greater than 0, indicating the end of the last word. If the count is 0, it continues iterating until a non-space character is found. Finally, it returns the count, which represents the length of the last word.

**Approach:**
1. Start iterating through the string from the end.
2. Keep track of the count of non-space characters encountered.
3. When encountering a non-space character, increment the count.
4. When encountering a space character, check if the count is greater than 0. If yes, return the count as it represents the length of the last word. If not, continue iterating.
5. Continue this process until the entire string is traversed.
6. If the loop terminates without finding any non-space character (count remains 0), return 0 as the last word length.

**Time Complexity:**
Let \( n \) be the length of the input string \( s \). The time complexity of the algorithm is \( O(n) \) because we iterate through the string once.

**Space Complexity:**
The space complexity of the algorithm is \( O(1) \) because we are using a constant amount of extra space, regardless of the input size. We only use a single integer variable (`count`) to store the length of the last word.


# Code
```
class Solution {
public:
    int lengthOfLastWord(string s) {
        int count = 0;
        for(int i=s.length() -1; i>=0; i--) {
            if(s[i] != ' ') count++;
            else {
                if (count > 0) return count;
            }
        }
        return count;
    }
};

```
