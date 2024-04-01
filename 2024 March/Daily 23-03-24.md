# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Always here to assist you guys.

## Today's 23-03-24 

## [143. Reorder List](https://leetcode.com/problems/reorder-list/description/?envType=daily-question&envId=2024-03-23)

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
My given code should aim to reorder a singly-linked list such that the resulting list is formed by interleaving the nodes from the first half and the reversed second half of the original list.

# Approach
<!-- Describe your approach to solving the problem. -->
- I finded the middle of the linked list.
- Reversed the second half of the list.
- Merged the first half and the reversed second half by alternating their nodes.
---
Have a look at the code , still have any confusion then please let me know in the comments ... Keep Solving.:)
# Complexity
- Time complexity : $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$n$ : size of linked list
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
  
  // Method to reorder the given linked list
  public void reorderList(ListNode head) {
  
    // Checking if the list is null or has only one node
    if (head == null || head.next == null){
      return;
    }

    // Finding the middle node of the list
    ListNode middle = findMiddle(head);
    // Reversing the second half of the list
    ListNode reversedSecondHalf = reverseList(middle);
    // Merging the first half and the reversed second half
    mergeLists(head, reversedSecondHalf);
  }

  // Method to find the middle node of the list
  private ListNode findMiddle(ListNode head) {
    ListNode prev = null;
    ListNode slowPtr = head;
    ListNode fastPtr = head;

    // Moving slowPtr by one and fastPtr by two until fastPtr reaches the end of the list
    while (fastPtr != null && fastPtr.next != null) {
      prev = slowPtr;
      slowPtr = slowPtr.next;
      fastPtr = fastPtr.next.next;
    }

    // Disconnecting the first half from the second half
    if (prev != null){
      prev.next = null;
    }

    return slowPtr; // Return the middle node
  }

  // Method to reverse a linked list
  static ListNode reverseList(ListNode head) {
    ListNode prev = null;
    ListNode current = head;

    // Reversing the list by updating pointers
    while (current != null) {
      ListNode nextNode = current.next;
      current.next = prev;
      prev = current;
      current = nextNode;
    }

    return prev; // Returning the new head of the reversed list
  }

  // Method to merge two linked lists by alternating their nodes
  static void mergeLists(ListNode first, ListNode second) {
    while (second != null) {
      ListNode nextFirst = first.next;
      first.next = second;
      first = second;
      second = nextFirst;
    }
  }
}
```
