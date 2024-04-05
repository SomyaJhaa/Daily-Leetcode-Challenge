# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Always here to assist you guys.

## Today's 05-04-24 

## [1544. Make The String Great](https://leetcode.com/problems/make-the-string-great/description/?envType=daily-question&envId=2024-04-05)

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
This problem requires removing pairs of adjacent characters from the input string if they have the same letter but different cases.

To solve the problem, I can use a stack (implemented as a linked list) to keep track of the characters that have not been removed.

# Approach
<!-- Describe your approach to solving the problem. -->
- I iterated through each character in the input string.
- For each character :
  - If the stack is not empty and the current character, when compared with the last character in the stack, forms a pair of characters with the same letter but different cases, I removed the last character from the stack.
  - If the current character and the next character (if exists) form a pair of characters with the same letter but different cases, I skipped the next character.
  - Otherwise, I added the current character to the stack.
- After processing all characters, I converted the characters remaining in the stack to a string, which represents the final result.
- Finally, I returned the final result string.

--- 
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)

# Complexity
- Time complexity : $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$n$ : length of the input string
- Space complexity : $O(n)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
   
    public String makeGood(String s) {
        
        // Converting the input string to a character array for easier manipulation.
        char[] chArr = s.toCharArray(); 
        
        // Initializing an empty string 'jawab' to store the final result.
        String jawab="";
        
        // Initializing a linked list to store characters.
        LinkedList<Character> linkedList = new LinkedList<>();
        
        // Looping through each character in the input string.
        for(int i = 0; i < chArr.length; i++){
            // If the linked list is not empty and the absolute difference between the last character in the linked list and the current character is equal to the difference between 'a' and 'A' (which represents the difference between lowercase and uppercase characters),
            // Removing the last character from the linked list and continue to the next iteration.
            if(!linkedList.isEmpty() && Math.abs(linkedList.getLast() - chArr[i]) == 'a' - 'A'){
                linkedList.removeLast(); 
                continue;
            }
            
            // If the current character and the next character (if exists) form a pair of characters with the same letter but different cases,
            // Skipping the next character and continue to the next iteration.
            if(i + 1 != chArr.length && Math.abs(chArr[i + 1] - chArr[i]) == 'a' - 'A') 
                i++;
            else 
                // Otherwise, adding the current character to the linked list.
                linkedList.add(chArr[i]);
        }
        
        // Converting the characters remaining in the linked list to a string and append them to the 'jawab' string.
        while(!linkedList.isEmpty()){
            jawab+=(linkedList.removeFirst());
        }
        
        // Returning the final result string.
        return jawab;
    }
}
```
