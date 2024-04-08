# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Always here to assist you guys.

## Today's 08-04-24

## [1700. Number of Students Unable to Eat Lunch](https://leetcode.com/problems/number-of-students-unable-to-eat-lunch/description/?envType=daily-question&envId=2024-04-08)

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
The task is to count the number of students who will be unable to get a sandwich. There are two types of sandwiches, circle, and square, represented by the integers 0 and 1 respectively. Students are also represented by integers, where 0 indicates a preference for circle sandwiches and 1 indicates a preference for square sandwiches. 

# Approach
<!-- Describe your approach to solving the problem. -->

**Counting Students** : 
   - I iterated through the `students` array and count the number of students preferring each type of sandwich. 
   - Maintained separate counters for circle and square sandwiches (`circleStudentCount` and `squareStudentCount`).

**Serving Sandwiches** :
   - Iterated through the `sandwiches` array.
   - For each sandwich :
     - If it's a circle sandwich (`sandwich == 0`), check if there are remaining students preferring circle sandwiches (`circleStudentCount > 0`).
       - If yes, serve the sandwich to a circle student by decrementing `circleStudentCount`.
       - If no circle students left, return the count of remaining square students (`squareStudentCount`).
     - If it's a square sandwich (`sandwich == 1`), check if there are remaining students preferring square sandwiches (`squareStudentCount > 0`).
       - If yes, serve the sandwich to a square student by decrementing `squareStudentCount`.
       - If no square students left, returned the count of remaining circle students (`circleStudentCount`).

**Return** : 
   - If all sandwiches are served successfully, returned 0, indicating no students are left without sandwiches.

--- 
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)

# Complexity
- Time complexity : $O(n + m)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$n$ : number of students
$m$ : number of sandwiches
- Space complexity : $O(1)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
    public int countStudents(int[] students, int[] sandwiches) {
        
        // Count of students preferring circle sandwiches
        int circleStudentCount = 0;
        // Count of students preferring square sandwiches
        int squareStudentCount = 0;

        // Counting the number of students preferring each type of sandwich
        for(int student : students) {
            if(student == 0) {
                circleStudentCount++;
            }
            else {
                squareStudentCount++;
            }
        }

        // Iterating through sandwiches and serving them to students
        for(int sandwich : sandwiches) {

            // If the sandwich type is circle and there are no more students preferring circle sandwiches, return the count of students preferring square sandwiches
            if(sandwich == 0 && circleStudentCount == 0) {
                return squareStudentCount;
            }
            // If the sandwich type is square and there are no more students preferring square sandwiches, return the count of students preferring circle sandwiches
            if(sandwich == 1 && squareStudentCount == 0) {
                return circleStudentCount;
            }
            // If the sandwich type is circle, serve it to a circle student and decrease the count of circle students
            if(sandwich == 0) {
                circleStudentCount--;
            }
            // If the sandwich type is square, serve it to a square student and decrease the count of square students
            else {
                squareStudentCount--;
            }
        }
        // All sandwiches have been served without any issues
        return 0;
    }
}

```
