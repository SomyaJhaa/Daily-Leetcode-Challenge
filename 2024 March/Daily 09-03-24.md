# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Always here to assist you guys.

## Today's 09-03-24 [Problem Link](https://leetcode.com/problems/minimum-common-value/description/?envType=daily-question&envId=2024-03-09)
## 2540. Minimum Common Value

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
The goal is to find the common element between two arrays, and my approach involves using a HashSet to efficiently check for common elements. My algorithm first determines which array is larger and populates the HashSet with elements from the smaller array. Then, it iterates through the larger array to find the common element by checking HashSet membership. Once found, the common element is returned.

# Approach
<!-- Describe your approach to solving the problem. -->
**Initialized the Variables :**
   - Initialized `common` to -1 to store the common element.
   - Initialized `n1IsLarge` to false to track which array is larger.

**Determined Larger Array :**
   - Checked if the length of `nums1` is greater than the length of `nums2`.
   - Set `n1IsLarge` to true if `nums1` is larger.

**Created HashSet :**
   - Created a HashSet `h` to store elements of the smaller array.

**Populated the HashSet :**
   - If `n1IsLarge` is true, iterated through `nums2` and added elements to HashSet `h`.
   - If `n1IsLarge` is false, iterated through `nums1` and added elements to HashSet `h`.

**Found Common Element :**
   - Iterated through the larger array.
   - If the current element is present in HashSet `h`, set `common` to that element and broke the loop.

**Result :**
   - Returned the value of `common`, which represents the common element.

---
Have a look at the code , still have any confusion then please let me know in the comments ... Keep Solving.:)
# Complexity
- Time complexity : $O(m + n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$m$ : length of smaller array


$n$ : length of larger array
- Space complexity : $O(m)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {

    public int getCommon(int[] nums1, int[] nums2) {
        int common = -1;
        boolean n1IsLarge = false;
        
        // Determining which array is larger
        if (nums1.length > nums2.length) {
            n1IsLarge = true;
        }
        
        HashSet<Integer> h = new HashSet<>();
        
        // Populating the HashSet with the elements of the smaller array
        if (n1IsLarge) {
            for (int i : nums2) {
                h.add(i);
            }
            
            // Finding the common element
            for (int i = 0; i < nums1.length; i++) {
                if (h.contains(nums1[i])) {
                    common = nums1[i];
                    break;
                }
            }
        } 
        else {
            for (int i : nums1) {
                h.add(i);
            }
            
            // Finding the common element
            for (int i = 0; i < nums2.length; i++) {
                if (h.contains(nums2[i])) {
                    common = nums2[i];
                    break;
                }
            }
        }
        
        return common;
    }
}
```