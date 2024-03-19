# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Always here to assist you guys.

## Today's 19-03-24 

## [621. Task Scheduler](https://leetcode.com/problems/task-scheduler/description/?envType=daily-question&envId=2024-03-19)

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
The problem requires us to determine the least interval needed to execute a given set of tasks, considering a cooldown period between tasks of the same type. 

# Approach
<!-- Describe your approach to solving the problem. -->
- I start by counting the frequency of each task. This allows us to identify the task with the maximum frequency.

- I calculate the total time required to execute all tasks with cooldown. This is determined by finding the maximum frequency task and accounting for the cooldown period between its executions.

- Next, I find the number of tasks that have the maximum frequency. This helps us understand how many tasks need to be executed with the maximum frequency.

- Finally, I determine the least interval by considering the maximum of either executing all tasks with cooldown or the total number of tasks. This ensures that I cover both scenarios where the cooldown is utilized and where it is not necessary.

By following this approach, I can efficiently calculate the least interval required to execute the tasks.

---
Have a look at the code , still have any confusion then please let me know in the comments ... Keep Solving.:)
# Complexity
- Time complexity : $O(t)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$t$ : number of tasks
- Space complexity : $O(26) = O(1)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
    
    // Static array to keep track of task frequencies
    static int[] frequencies;
    
    public int leastInterval(char[] tasks, int n) {
        
        // Initializing the frequency array to keep track of task occurrences
        frequencies = new int[26];

        // Populating the frequency array by iterating through the tasks
        for (char task : tasks) {
            frequencies[task - 'A']++;
        }   

        // Finding the maximum frequency of any task
        int maxFrequency = Arrays.stream(frequencies).max().getAsInt();
        
        // Calculating the total time taken for executing all tasks with cooldown
        int totalWithCooldown = (maxFrequency - 1) * (n + 1);
        
        // Calculating the number of tasks that have the maximum frequency
        int numOfMaxFrequency = (int) Arrays.stream(frequencies).filter(f -> f == maxFrequency).count();
        
        // Returning the maximum of either executing all tasks with cooldown or total number of tasks
        return Math.max(totalWithCooldown + numOfMaxFrequency, tasks.length);
    }
}
```
