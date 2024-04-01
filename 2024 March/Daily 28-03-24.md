# Daily Leetcode Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Always here to assist you guys.

## Today's 28-03-24

## [2958. Length of Longest Subarray With at Most K Frequency](https://leetcode.com/problems/length-of-longest-subarray-with-at-most-k-frequency/description/?envType=daily-question&envId=2024-03-28)

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
My algorithm should employ a sliding window technique to find the maximum subarray length whose sum equals a given target `k`.
# Approach
<!-- Describe your approach to solving the problem. -->
**Initialization** : I initialized a HashMap to store the frequency of elements encountered and variables to track the start index of the subarray (`s`) and the maximum length found so far (`jawab`).

**Iterated Through Array** : Traversed the input array `nums`.

**Updated HashMap** : Updated the frequency of the current element in the HashMap using the `merge()` method.

**Checked Subarray Sum** : Checked if the sum of elements from the start index to the current index equals `k`.

**Adjusted Start Index** : If the sum exceeded `k`, moved the start index forward and updated the HashMap accordingly.

**Updated Maximum Length** : Updated the maximum length found so far (`jawab`) using the `Math.max()` function.

**Result** : Returned the maximum subarray length satisfying the condition (`jawab`).

--- 
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)
# Complexity
- Time complexity : $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$n$ : number of elements in the array
- Space complexity : $O(u)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
$u$ : number of unique elements in the array

# Code
```
class Solution {

    // Static HashMap to store the frequency of elements encountered
    static HashMap<Integer, Integer> m;
    
    // Static variable to store the maximum subarray length satisfying the condition
    static int jawab;

    // Method to find the maximum subarray length whose sum equals k
    public int maxSubarrayLength(int[] nums, int k) {
        // Initializing the HashMap
        m = new HashMap<>();
        // Initializing variables to track the start index of the subarray and the maximum length found so far
        int s = 0;
        jawab = 0;

        // Traversing the array
        for (int i = 0; i < nums.length; i++) {
            // Updating the frequency of the current element in the HashMap
            m.merge(nums[i], 1, Integer::sum);
            
            // Checking if the sum of elements from start index to current index equals k
            while (m.get(nums[i]) == 1 + k) {
                // If sum exceeds k, moving the start index forward and updating the HashMap accordingly
                m.merge(nums[s], -1, Integer::sum);
                s++;
            }
            
            // Updating the maximum length found so far
            jawab = Math.max(jawab, i - s + 1);
        }
        
        // Returning the maximum subarray length satisfying the condition
        return jawab;
    }
}
```
