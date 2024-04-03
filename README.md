# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Always here to assist you guys.

<<<<<<< HEAD
## Today's 03-04-24 

## [79. Word Search](https://leetcode.com/problems/word-search/description/?envType=daily-question&envId=2024-04-03)

### Intuition:
The problem asks to find if the given word can be constructed from letters of sequentially adjacent cells in the grid. We can start from each cell of the grid and perform a depth-first search (DFS) to check if the current cell matches the first character of the word. If it does, we continue the search recursively by checking horizontally and vertically neighboring cells to match the subsequent characters of the word.

### Approach:
1. Start a DFS from each cell of the grid.
2. In the DFS, check if the current cell matches the character of the word at the current index.
3. If it does, mark the cell as visited (to avoid reusing it) and continue DFS recursively to check neighboring cells.
4. If the current index reaches the length of the word, return true (indicating that the word is found).
5. After DFS, revert the changes made to the visited cells to backtrack for other possible paths.
6. Repeat the process for all cells in the grid.
7. If no matching word is found after exploring all cells, return false.

### Time Complexity:
Let $m$ be the number of rows in the grid, $n$ be the number of columns, and $l$ be the length of the word.
- The DFS is performed for each cell in the $m \times n$ grid, resulting in a time complexity of $O(m \cdot n)$.
- In each DFS, the maximum recursion depth is bounded by the length of the word ($l$).
- Within each DFS call, constant-time operations are performed.
- Thus, the overall time complexity is $O(m \cdot n \cdot l)$.

### Space Complexity:
- The space complexity is determined by the recursion stack during DFS.
- The maximum depth of the recursion stack is bounded by the length of the word ($l$).
- Additionally, a constant amount of extra space is used for storing the grid.
- Therefore, the space complexity is $O(l)$.
=======
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
>>>>>>> cb78c6e2b0be01e08c6a855cf80388dd9bf1533a

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
<<<<<<< HEAD
 public:
  bool exist(vector<vector<char>>& board, string word) {
    for (int i = 0; i < board.size(); ++i)
      for (int j = 0; j < board[0].size(); ++j)
        if (dfs(board, word, i, j, 0))
          return true;
    return false;
  }

 private:
  bool dfs(vector<vector<char>>& board, const string& word, int i, int j,
           int s) {
    if (i < 0 || i == board.size() || j < 0 || j == board[0].size())
      return false;
    if (board[i][j] != word[s] || board[i][j] == '*')
      return false;
    if (s == word.length() - 1)
      return true;

    const char cache = board[i][j];
    board[i][j] = '*';
    const bool isExist = dfs(board, word, i + 1, j, s + 1) ||
                         dfs(board, word, i - 1, j, s + 1) ||
                         dfs(board, word, i, j + 1, s + 1) ||
                         dfs(board, word, i, j - 1, s + 1);
    board[i][j] = cache;

    return isExist;
  }
};

=======
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
>>>>>>> cb78c6e2b0be01e08c6a855cf80388dd9bf1533a
```
