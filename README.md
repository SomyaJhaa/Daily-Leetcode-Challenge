# Daily Leetcode Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Always here to assist you guys.

## Today's 30-03-24

## [992. Subarrays with K Different Integers](https://leetcode.com/problems/subarrays-with-k-different-integers/description/?envType=daily-question&envId=2024-03-30)

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
This problem can be solved using a sliding window approach combined with hashing.
# Approach
<!-- Describe your approach to solving the problem. -->
- I defined a helper function `subarrayAtmostKdistinct` which calculates the number of subarrays with at most `k` distinct elements.
- The main function `subarraysWithKDistinct` then calculates the number of subarrays with exactly `k` distinct elements by subtracting the count of subarrays with at most `k-1` distinct elements from the count of subarrays with at most `k` distinct elements.
- I used a sliding window approach where I kept track of the frequency of elements within the current window using a hashmap.
- I iterated through the array using two pointers `start` and `end`, where `start` marks the start of the current window and `end` marks the end.
- I incremented `end` until the number of distinct elements within the window exceeded `k`.
- At each step, I updated the hashmap and calculated the count of subarrays with at most `k` distinct elements using the formula `end - start + 1`.
- I repeated this process until I reached the end of the array.

By following this approach, I efficiently calculated the number of subarrays with exactly `k` distinct elements.

--- 
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)
# Complexity
- Time complexity : $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$n$ : length of the input array
- Space complexity : $O(k)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
$k$ : given
# Code
```
class Solution {
    public static int subarraysWithKDistinct(int[] nums, int k) {

        return subarrayAtmostKdistinct(nums, k) - subarrayAtmostKdistinct(nums, k-1);
        
    }

    public static int subarrayAtmostKdistinct( int[] a, int k){      // this function will give number of subarrays which have at most 'k' distinct elements
        int count = 0; 
        HashMap<Integer, Integer> h = new HashMap<>();           // to store the occurences of numbers
        int start = 0;                                 // to be considered when number of distinct numbers crosses 'k'
        for( int end = 0; end < a.length; end++){
            h.put( a[end], h.getOrDefault(a[end], 0) + 1);  
            while( h.size() > k){
                int t = h.get(a[start]);    // get the number of occurences of leftmost number
                h.put(a[start], t-1);       // decrement it's number of occurence
                if( t-1 == 0){              // if it was the last of it's kind then remove this from hashmap
                    h.remove(a[start]);
                } 
                start++;                // incremented the start
            }
            count += end - start + 1;  // try to visualise with {1,2,1,3,4} with k = 3 then you will get why this (end-start+1) is added : because it will give the all subarrays with distinct numbers less than or equal to 'k'
        }
        return count;
    }

}
```
