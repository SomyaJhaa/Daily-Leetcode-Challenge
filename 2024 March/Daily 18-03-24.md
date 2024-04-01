# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Always here to assist you guys.

## Today's 18-03-24 

## [452. Minimum Number of Arrows to Burst Balloons](https://leetcode.com/problems/minimum-number-of-arrows-to-burst-balloons/description/?envType=daily-question&envId=2024-03-18)

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
- Sort the points based on their end coordinates to efficiently burst balloons.
- Iterate through the sorted array, updating the arrow position to burst overlapping balloons.
- Increment the arrow count whenever a new arrow is needed.
# Approach
<!-- Describe your approach to solving the problem. -->

**Sorted Points :** Sorted the points based on their end coordinates using a custom comparator.

**Initialized Variables :** Initialized variables for the arrow count and current arrow position.

**Iterate Through Points :** Iterated through the sorted array of points.

**Checked Balloon Positions :** For each point, checked if its start coordinate is greater than the current arrow position.

**Updated Arrow Position :** If the start coordinate of the current point is greater than the current arrow position, updated the arrow position to the end coordinate of the current point.

**Incremented Arrow Count :** Incremented the arrow count whenever a new arrow is needed to burst a balloon.

**Result :** After iterating through all points, returned the arrow count as the minimum number of arrows needed.

---
Have a look at the code , still have any confusion then please let me know in the comments ... Keep Solving.:)
# Complexity
- Time complexity : $O(n * logn )$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$n$ : number of points
- Space complexity : $O(1)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
  public int findMinArrowShots(int[][] points) {
    
    // Sorting points based on their end coordinates
    Arrays.sort(points, (a, b) -> Integer.compare(a[1], b[1]));

    // Initializing variables
    int jawab = 1;
    int teer = points[0][1];

    // Iterating through the sorted array of points
    for (int i = 1; i < points.length; ++i) {
      // If the start coordinate of the current point is greater than the current arrow position
      if (points[i][0] > teer) {
        // Updating the current arrow position to the end coordinate of the current point
        teer = points[i][1];
        // Incrementing the arrow count
        jawab++;
      }
    }

    // Returning the arrow count as the result
    return jawab;
  }
}
```
