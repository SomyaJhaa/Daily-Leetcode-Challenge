# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Always here to assist you guys.

## Today's 13-04-24

## [85. Maximal Rectangle](https://leetcode.com/problems/maximal-rectangle/description/?envType=daily-question&envId=2024-04-13)

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
The problem involves finding the maximal rectangle containing only 1s in a binary matrix. To solve this problem efficiently, I can utilize the concept of histograms. For each row in the matrix, I can treat it as the base of a histogram and calculate the height of bars in the histogram based on the consecutive 1s in that row. Then, I can apply the largest rectangle in histogram algorithm to find the maximal rectangle for each row. Finally, I return the maximum area among all rows as the result.

# Approach
<!-- Describe your approach to solving the problem. -->

- I initialized a variable to store the maximal rectangle area.
- Iterate through each row in the matrix:
    - Update the histogram of heights for each row. Treat 1s as bars and consecutive 1s as increasing heights in the histogram.
    - Calculate the maximal rectangle area using the largest rectangle in histogram algorithm for the current histogram.
    - Update the maximal rectangle area if the current area is greater.
- Return the maximal rectangle area as the result.

##### Largest Rectangle in Histogram Algorithm :
- I nitialized a stack to store the indices of histogram bars.
- Iterated through each bar in the histogram:
    - If the stack is empty or the current bar's height is greater than or equal to the height of the bar at the top of the stack, push the index of the current bar onto the stack.
    - If the current bar's height is less than the height of the bar at the top of the stack, keep popping bars from the stack until the stack is empty or the height of the bar at the top of the stack is less than the current bar's height. For each popped bar, calculate its area using the popped height as the height of the rectangle and the difference between the current index and the index of the bar at the top of the stack as the width of the rectangle. Update the maximal rectangle area if the calculated area is greater.
- After iterating through all bars, if there are bars left in the stack, repeat step 2 for each remaining bar.
- Returned the maximal rectangle area calculated.

--- 
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)

# Complexity
- Time complexity : $O(m*n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$m$ : number of rows

$n$ : number of columns
- Space complexity : $O(n)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
    
    // Method to find the maximal rectangle area in a given matrix
    public int maximalRectangle(char[][] matrix) {

        // Check if the matrix is null or empty
        if (matrix == null || matrix.length == 0) {
            return 0;
        }
        
        // Initialize the maximal rectangle area
        int maxArea = 0;
        // Initialize an array to store the histogram of heights
        int[] heights = new int[matrix[0].length];
        
        // Iterate through each row in the matrix
        for (char[] row : matrix) {
            // Update the histogram for each row
            for (int i = 0; i < row.length; i++) {
                heights[i] = row[i] == '0' ? 0 : heights[i] + 1;
            }
            // Update the maximal rectangle area
            maxArea = Math.max(maxArea, calculateMaxArea(heights));
        }
        
        return maxArea;
    }
    
    // Method to calculate the maximal rectangle area using histogram
    private int calculateMaxArea(int[] heights) {

        // Initialize the maximal rectangle area
        int maxArea = 0;
        // Initialize a stack to store the indices of heights
        Stack<Integer> stack = new Stack<>();
        
        // Iterate through each height and calculate the maximal rectangle area
        for (int i = 0; i <= heights.length; i++) {
            // Check if the stack is not empty and the current height is less than the height at the top of the stack
            while (!stack.isEmpty() && (i == heights.length || heights[stack.peek()] > heights[i])) {
                // Get the height at the top of the stack
                int currentHeight = heights[stack.pop()];
                // Calculate the width of the rectangle
                int width = stack.isEmpty() ? i : i - stack.peek() - 1;
                // Update the maximal rectangle area
                maxArea = Math.max(maxArea, currentHeight * width);
            }
            // Push the index of the current height onto the stack
            stack.push(i);
        }
        
        return maxArea;
    }
}
```
