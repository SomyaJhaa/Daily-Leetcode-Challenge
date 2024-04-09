# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Always here to assist you guys.

## Today's 09-04-24

## [2073. Time Needed to Buy Tickets](https://leetcode.com/problems/time-needed-to-buy-tickets/description/?envType=daily-question&envId=2024-04-09)

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
Given a queue of ticket prices and a special position \( k \), the problem asks to calculate the total time required to buy tickets. If a person is at or before position \( k \), they buy tickets at the \( k \)-th price; otherwise, they buy at \( k \)-th price minus 1.

# Approach
<!-- Describe your approach to solving the problem. -->
- I initialized total time to 0.
- Iterated through the queue:
  - For positions before or at \( k \), buy tickets at \( k \)-th price.
  - For positions after \( k \), buy tickets at \( k \)-th price minus 1.
- Accumulated the time taken for each purchase.
- Returned the total time.

--- 
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)

# Complexity
- Time complexity : $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$n$ : number of tickets
- Space complexity : $O(1)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {

    // Method to calculate the total time required to buy tickets
    public int timeRequiredToBuy(int[] tickets, int k) {
        // Variable to store the total time
        int totalTime = 0;
        
        // Looping through each ticket price
        for (int i = 0; i < tickets.length; i++) {
            
            // If the person is at or before the k-th position in the queue
            if (i <= k) {
                
                // Adding the minimum of the ticket price at the current position and the price at the k-th position to the total time
                totalTime += Math.min(tickets[i], tickets[k]);
            }

            // If the person is after the k-th position in the queue
            if (i > k) {
               
                // Adding the minimum of the ticket price at the current position and the price at the k-th position minus 1 to the total time
                totalTime += Math.min(tickets[i], tickets[k] - 1);
            }
        }
        
        // Returning the total time required to buy tickets
        return totalTime;
    }
}
```
