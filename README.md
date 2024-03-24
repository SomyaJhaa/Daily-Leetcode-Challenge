# Happy Holika Dahan! May the flames of this sacred fire ignite hope, love, and prosperity in your life. 🪔✨ #HolikaDahan

# Daily Leetcode Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Always here to assist you guys.

## Today's 24-03-24 

## [287. Find the Duplicate Number](https://leetcode.com/problems/find-the-duplicate-number/description/?envType=daily-question&envId=2024-03-24)

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
To solve this problem, I should iterate through the array `nums` and use a HashSet to keep track of the numbers we have encountered so far. 

# Approach
<!-- Describe your approach to solving the problem. -->
- I initialized an empty HashSet `hs`.
- I iterated through each element `num` in the array `nums`.
- For each element `num`, we check if it is already present in the HashSet `hs` using the `add` method.
   - If `num` is already present in `hs`, the `add` method will return `false`, indicating that `num` is a duplicate.
     - In this case, I return `num` as it is the duplicate element.
   - If `num` is not present in `hs`, I add it to the HashSet and continue with the next iteration.

Finally, if no duplicate is found after iterating through the entire array, I return `-1` to indicate that no duplicates exist in the array.

---
Have a look at the code , still have any confusion then please let me know in the comments ... Keep Solving.:)
# Complexity
- Time complexity : $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$n$ : number of elements in the input array `nums`
- Space complexity : $O(n)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
    
    public int findDuplicate(int[] nums) {    
        // HashSet to store encountered numbers
        HashSet<Integer> hs = new HashSet<>();
        
        // Length of the array
        int length = nums.length;
        
        // Iterating through the array
        for (int i = 0; i < length; i++) {
            // If the number is already in the HashSet, it's a duplicate
            if (!hs.add(nums[i])) {
                return nums[i];
            }
        }
        
        // If no duplicates found, return -1
        return -1;
    }
}
```
