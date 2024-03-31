# Daily Leetcode Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Always here to assist you guys.

## Today's 31-03-24

## [2444. Count Subarrays With Fixed Bounds](https://leetcode.com/problems/count-subarrays-with-fixed-bounds/description/?envType=daily-question&envId=2024-03-31)

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
The problem requires counting the number of subarrays within a given range [minK, maxK] where the subarray's elements are also within this range. To efficiently count these subarrays, I can iterate through the array once and keep track of the last invalid index, the last occurrence of minK, and the last occurrence of maxK. By doing so, I can determine the valid subarrays that end at each index.

# Approach
<!-- Describe your approach to solving the problem. -->

- Initialized variables :
   - `count`: to store the count of valid subarrays.
   - `lastInvalidIndex`: to keep track of the index of the last element that violates the range condition.
   - `lastMinIndex`: to store the index of the last occurrence of minK.
   - `lastMaxIndex`: to store the index of the last occurrence of maxK.

- Iterated through the array `nums` :
   - Updated `lastInvalidIndex` if the current element is out of the range [minK, maxK].
   - Updated `lastMinIndex` if the current element is equal to minK.
   - Updated `lastMaxIndex` if the current element is equal to maxK.
   - Calculated the count of valid subarrays up to the current index by taking the maximum of 0 and the difference between the minimum of `lastMinIndex` and `lastMaxIndex` and `lastInvalidIndex`.
   - Added this count to the `count`.

- Returned the total count of valid subarrays.

By following this approach, I can efficiently count the number of valid subarrays within the given range.

--- 
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)
# Complexity
- Time complexity : $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$n$ : length of the input array `nums`
- Space complexity : $O(1)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {

    // Function to count subarrays within the given range [minK, maxK]
    public long countSubarrays(int[] nums, int minK, int maxK) {

        // Variable to store the count of valid subarrays
        long count = 0;
        // Index of the last element that violates the range condition
        int lastInvalidIndex = -1;
        // Index of the last occurrence of minK
        int lastMinIndex = -1;
        // Index of the last occurrence of maxK
        int lastMaxIndex = -1;

        // Iterating through the array
        for (int i = 0; i < nums.length; ++i) {
            // Updating lastInvalidIndex if current element is out of range
            if (nums[i] < minK || nums[i] > maxK) {
                lastInvalidIndex = i;
            }
            // Updating lastMinIndex if current element is equal to minK
            if (nums[i] == minK) {
                lastMinIndex = i;
            }
            // Updating lastMaxIndex if current element is equal to maxK
            if (nums[i] == maxK) {
                lastMaxIndex = i;
            }
            // Calculating the count of valid subarrays up to the current index
            count += Math.max(0, Math.min(lastMinIndex, lastMaxIndex) - lastInvalidIndex);
        }
        // Returning the total count of valid subarrays
        return count;
    }
}
```
