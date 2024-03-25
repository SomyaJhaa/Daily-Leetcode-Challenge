# 🎨🌈 Wishing You a Colorful Holi ! 🎉🎆
## May your journey through the repository be as bright and joyful as the colors of Holi ! Happy Holi to all our viewers ! 🌺💫

# Daily Leetcode Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Always here to assist you guys.

## Today's 25-03-24 

## [442. Find All Duplicates in an Array](https://leetcode.com/problems/find-all-duplicates-in-an-array/description/?envType=daily-question&envId=2024-03-25)

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
- My algorithm should marks encountered numbers by toggling their sign at the index corresponding to their absolute value.
- Positive values at these indices should indicate duplicate numbers.
# Approach
<!-- Describe your approach to solving the problem. -->
- I iterated through each number in the array.
- Toggle the sign of the number at the index corresponding to its absolute value.
- If the number at that index is positive, it means it has been encountered before, so added the absolute value of the number to the duplicates list.
- Returned the list of duplicates.

---
Have a look at the code , still have any confusion then please let me know in the comments ... Keep Solving.:)
# Complexity
- Time complexity : $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$n$ : length of the input array
- Space complexity : $O(1)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {

  // Method to find duplicates in an array of integers
  public List<Integer> findDuplicates(int[] numbers) {
   
    // List to store duplicates
    List<Integer> duplicates = new ArrayList<>();

    // Iterating through each number in the array
    for (final int number : numbers) {
      // Toggling the sign of the number at the index corresponding to its absolute value
      numbers[Math.abs(number) - 1] *= -1;
      
      // If the number at that index is positive, it means it has been encountered before
      if (numbers[Math.abs(number) - 1] > 0){
        // Adding the absolute value of the number to the duplicates list
        duplicates.add(Math.abs(number));
      }
    }
    
    // Returning the list of duplicates
    return duplicates;
  }
}
```
