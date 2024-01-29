
# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.


## Always here to assist you guys.

## Today's 29-01-24 
## [232. Implement Queue using Stacks](https://leetcode.com/problems/implement-queue-using-stacks/description/?envType=daily-question&envId=2024-01-29)

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
My code implements a queue data structure using two stacks (`andar` and `bahar`). A queue follows the First-In-First-Out (FIFO) principle, and stacks follow the Last-In-First-Out (LIFO) principle. By utilizing two stacks cleverly, I can simulate the behavior of a queue efficiently.

# Approach
<!-- Describe your approach to solving the problem. -->
**Initialization :**
  - Two stacks, andar and bahar, represent the input and output of the queue.

**Push Operation (push method) :**
  - Added elements to the input stack (andar), representing the enqueue operation.

**Pop Operation (pop method) :**
  - Ensured the output stack (bahar) is populated before popping an element.
  - Called the peek method to populate the output stack if needed and then pops the front element.

**Peek Operation (peek method) :**
  - Transferred elements from the input stack to the output stack if the output stack is empty.
  - Ensured the front element of the queue is always at the top of the output stack.
  - Returned the front element without removing it.

**Empty Check (empty method) :**
  - Checked if both the input and output stacks are empty, indicating an empty queue.
  - 
My implementation provides an efficient way to simulate the behavior of a queue using two stacks while maintaining the FIFO order of elements.

# Complexity
- Time complexity : $O(1)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity : $O(e)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
$e$ : number of elements in the queue

# Code
```
import java.util.ArrayDeque;
import java.util.Deque;

// Implementation of a queue using two stacks
class MyQueue {
  // Two stacks to represent the queue
  private Deque<Integer> andar = new ArrayDeque<>();
  private Deque<Integer> bahar = new ArrayDeque<>();
  
  // Method to push an element onto the queue
  public void push(int x) {
    andar.push(x);
  }

  // Method to pop an element from the queue
  public int pop() {
    // Ensuring the output stack is populated before popping
    peek();
    return bahar.pop();
  }

  // Method to peek at the front element of the queue
  public int peek() {
    // If the output stack is empty, transferring elements from input to output
    if (bahar.isEmpty()) {
      while (!andar.isEmpty()) {
        bahar.push(andar.pop());
      }
    }
    return bahar.peek();
  }

  // Method to check if the queue is empty
  public boolean empty() {
    return andar.isEmpty() && bahar.isEmpty();
  }
}

```
