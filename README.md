# Daily Leetcode Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Always here to assist you guys.

## Today's 27-03=24 

## [713. Subarray Product Less Than K](https://leetcode.com/problems/subarray-product-less-than-k/description/?envType=daily-question&envId=2024-03-27)

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
The problem requires finding the number of subarrays with a product less than a given threshold `k`. I can solve this efficiently using the sliding window technique.

# Approach
<!-- Describe your approach to solving the problem. -->
**Initialization** : I initialized two pointers `l` and `r` to track the left and right ends of the sliding window, respectively. Initialize `guna` (product of subarrays) and `jawab` (count of valid subarrays) to 1 and 0, respectively.

**Edge Case Handling** : If `k` is less than or equal to 1, returned 0 as there can be no subarrays with product less than `k`.

**Sliding Window Technique** : Iterated through the array using the right pointer `r`. At each step :
- Updated `guna` by multiplying it with the current element `nums[r]`.
- If `guna` becomes greater than or equal to `k`, shrink the window from the left :
    - Moved the left pointer `l` to the right and divide `guna` by `nums[l]` until `guna` is less than `k`.
- Added the count of valid subarrays (`r - l + 1`) to `jawab`.
- Moved the right pointer `r` to the next element.

**Return** : After iterating through the array, returned the count of valid subarrays `jawab`.

--- 
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)
# Complexity
- Time complexity : $O(N)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$N$ : number of elements in the input array `nums`
- Space complexity : $O(1)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {

    // Static variables to store the product of subarrays and the count of valid subarrays
    static int guna;
    static int jawab;
    
    // Method to count the number of subarrays with product less than k
    public int numSubarrayProductLessThanK(int[] nums, int k) {
    
        // If k is less than or equal to 1, there can be no subarrays with product less than k
        if( k <= 1){
            return 0;
        }
        
        // Initializing the product of subarrays and the count of valid subarrays
        guna = 1;
        jawab = 0;
        
        // Initializing pointers for the sliding window technique
        int l = 0; // Left pointer
        int r = 0; // Right pointer
        
        // Iterating through the array
        while( r < nums.length){

            // Multiplying the product of subarrays with the current element
            guna *= nums[r];
            
            // If the product becomes greater than or equal to k, shrinking the window from the left
            while( guna >= k){
                guna /= nums[l++]; // Dividing the product by the element at the left pointer
            }
            
            // Adding the count of valid subarrays to the answer
            jawab += r - l + 1;
            
            // Moving the right pointer to the next element
            r++;
        }
        
        // Returning the count of valid subarrays
        return jawab;
    }
}
```
