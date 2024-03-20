# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Always here to assist you guys.

## Today's 20-03-24 

## [1669. Merge In Between Linked Lists](https://leetcode.com/problems/merge-in-between-linked-lists/description/?envType=daily-question&envId=2024-03-20)

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
The task is to merge the nodes of `head2` into `head1` between the indices `start` and `end`.

# Approach
<!-- Describe your approach to solving the problem. -->

- I initialized a pointer `beforeStartNode` to `head1`.
- Moved `beforeStartNode` to the node before the `start` index by iterating `start - 1` times.
- Initialized a pointer `endNode` to the node at the `start` index (i.e., `beforeStartNode.next`).
- Moved `endNode` to the node at the `end` index by iterating `end - start` times.
- Connected the node before the `start` index to the head of `head2`.
- Finded the last node in `head2` by traversing till the end of the list.
- Connected the last node of `head2` to the node after the `end` index.
- Disconnected the nodes between the `start` and `end` indices from `head1`.
- Returned the modified `head1` after merging `head2` between `start` and `end` indices.

---
Have a look at the code , still have any confusion then please let me know in the comments ... Keep Solving.:)
# Complexity
- Time complexity : $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$n$ :  number of nodes in the list
- Space complexity : $O(1)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
  
  // Function to merge the nodes of head2 into head1 between the indices start and end
  public ListNode mergeInBetween(ListNode head1, int start, int end, ListNode head2) {
    
    // Pointer to the node before the start index
    ListNode beforeStartNode = head1;
    for (int i = 0; i < start - 1; i++){
      beforeStartNode = beforeStartNode.next;
    }

    // Pointer to the node at the end index
    ListNode endNode = beforeStartNode.next;
    for (int i = 0; i < end - start; i++){
      endNode = endNode.next;
    }

    // Connecting the node before the start index to the head of head2
    beforeStartNode.next = head2;
    
    // Finding the last node in head2
    ListNode lastNodeInHead2 = head2;
    while (lastNodeInHead2.next != null){
      lastNodeInHead2 = lastNodeInHead2.next;
    }

    // Connecting the last node of head2 to the node after the end index
    lastNodeInHead2.next = endNode.next;
    
    // Disconnecting the nodes between the start and end indices from head1
    endNode.next = null;
    
    // Returning the modified head1 after merging head2 between start and end indices
    return head1;
  }
}
```
