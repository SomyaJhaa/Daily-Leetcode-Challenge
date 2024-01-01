# Leetcode Daily Challenge Solutions

This is my attemp to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.


## A very Happy Near Year to all you guys, may god give you strength to overcome what you want.
## Always here to assist you guys.

## Todays 01-01-24 [Problem Link](https://leetcode.com/problems/assign-cookies/description/?envType=daily-question&envId=2024-01-01)

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
Unitary method.

# Approach
<!-- Describe your approach to solving the problem. -->
- I sorted both arrays - 'g' & 's'
- Started from first element of 'g' 
- - checked from first element for element greater than 'g[i]' in 's[j]'
- - if found then incremented the count and nullify that 's[j]' so that that cookie cann't be considered in next child
- Ran this loop for all elements of 'g'
---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)
 
# Complexity
- Time complexity : $$O(gs)$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity : $$O(1)$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
    public int findContentChildren(int[] g, int[] s) {
        // sorting both the arrays
        Arrays.sort(g);
        Arrays.sort(s);
        int c = 0;      // to store the number of contended children
        for( int i = 0; i < g.length; i++){
            for( int j = 0; j < s.length; j++){
                if( s[j] >= g[i]){
                    c++;
                    s[j] = 0;
                    break;
                }
            }
        }
        return c;
    }
}
```
