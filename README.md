## Today's 06-02-24 
## [49. Group Anagrams](https://leetcode.com/problems/group-anagrams/description/?envType=daily-question&envId=2024-02-06)

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
The goal of my algorithm is to group anagrams from a given array of strings. Two strings are considered anagrams if they can be rearranged to form the same string.


# Approach
<!-- Describe your approach to solving the problem. -->

**Initialized the HashMap** : Created a HashMap (`m`) to store anagrams grouped by their sorted representations.

**Iterated Through Strings** : Looped through each string (`str`) in the input array.

**Sorted the Characters** : Converted the string to a character array (`c`) and sorted it. This ensured that anagrams have the same sorted representation.

    ```java
    char[] c = str.toCharArray();
    Arrays.sort(c);
    String s = new String(c);
    ```

**Group Anagrams** : Used `computeIfAbsent` to add the sorted representation (`s`) as a key in the HashMap. If the key is absent, created a new `ArrayList` as the value. Added the original string to the corresponding list.

    ```java
    m.computeIfAbsent(s, p -> new ArrayList<>()).add(str);
    ```

    Alternatively, I could have used `putIfAbsent` and `get`:

    ```java
    // m.putIfAbsent(s, new ArrayList<>());
    // m.get(s).add(str);
    ```

**Returned the Result** :  After processing all strings, returned the grouped anagrams as a list of lists.

    ```java
    return new ArrayList<>(m.values());
    ```

My approach ensured that anagrams are grouped together based on their sorted representations, allowing for efficient grouping and retrieval.

---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)
# Complexity
- Time complexity : $O(N⋅K⋅log(K))$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$N$ : number of strings in the input array.

$K$ : maximum length of a string.
- Space complexity : $O(M)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
$M$ : number of unique sorted representations.

# Code
```
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        
        // Initializing a HashMap to store anagrams grouped by their sorted representations
        HashMap<String, List<String>> m = new HashMap<>();

        // Iterating through each string in the input array
        for (String str : strs) {
            // Converting the string to a char array and sort it
            char[] c = str.toCharArray();
            Arrays.sort(c);
            String s = new String(c);
            
            // Using computeIfAbsent to add the sorted representation as a key
            // If the key is absent, it will create a new ArrayList as the value and add the original string to the corresponding list
            m.computeIfAbsent(s, p -> new ArrayList<>()).add(str);

            // Alternative approach using putIfAbsent and get
            //m.putIfAbsent(s, new ArrayList<>());
            //m.get(s).add(str);
        }

        // Returning the grouped anagrams as a list of lists
        return new ArrayList<>(m.values());
    }
}

```
