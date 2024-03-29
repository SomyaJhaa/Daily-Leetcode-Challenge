# Daily Leetcode Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Always here to assist you guys.

## Today's 29-03-24

## [2962. Count Subarrays Where Max Element Appears at Least K Times](https://leetcode.com/problems/count-subarrays-where-max-element-appears-at-least-k-times/description/?envType=daily-question&envId=2024-03-29)

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
My given solution should aim to count the number of subarrays in an array `arr` with at least `k` occurrences of the maximum element.

# Approach
<!-- Describe your approach to solving the problem. -->
**Initialization** :
   - Initialized `length` as the length of `arr`.
   - Initialized `maxValue` to store the maximum value in `arr`.
   - Initialized `left` and `right` pointers for the sliding window approach.
   - Initialized `ginti` to count occurrences of the maximum value.
   - Initialized `jawab` to accumulate the count of valid subarrays.

**Fonded the Maximum Value** :
   - Iterated through `arr` to find the maximum value, stored in `maxValue`.

**Sliding Window Approach** :
   - Initialized `left` and `right` pointers to traverse the array.
   - Initialized `ginti` to track the count of occurrences of the maximum value in the current window.
   - Iterated through the array using `right` pointer:
     - Incremented `ginti` if `arr[right]` equals `maxValue`.
     - If `ginti` becomes greater than or equal to `k` :
       - Incremented `jawab` by the count of valid subarrays ending at `right`.
       - Slided the window by incrementing `left` until `ginti` becomes less than `k`.
   - Repeated the process until `right` reaches the end of the array.

**Result** :
   - Returned the final count stored in `jawab`.

--- 
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)
# Complexity
- Time complexity : $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$n$ : length of the input array `arr`
- Space complexity : $O(1)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
    public long countSubarrays(int[] arr, int k) {
        int length = arr.length;
        int maxValue = Integer.MIN_VALUE;
        
        // Finding the maximum value in the array
        for (int num : arr) {
            maxValue = Math.max(maxValue, num);
        }
        
        int left = 0, right = 0, ginti = 0;
        long jawab = 0;

        // Sliding window approach
        while (right < length) {
            // Incrementing ginti if the element is equal to the maximum value
            if (arr[right] == maxValue) {
                ginti++;
            }
            // Checking if ginti is greater than or equal to k
            if (ginti >= k) {
                // Moving the left pointer until ginti is less than k
                while (ginti >= k) {
                    // Incrementing jawab by the ginti of valid subarrays
                    jawab += length - right;
                    // Decrementing ginti if the element at left is equal to the maximum value
                    if (arr[left] == maxValue) {
                        ginti--;
                    }
                    left++;
                }
            }
            right++;
        }
        return jawab;
    }
}
```
