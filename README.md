# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Always here to assist you guys.

## Today's 22-03-24 

## [234. Palindrome Linked List](https://leetcode.com/problems/palindrome-linked-list/description/?envType=daily-question&envId=2024-03-22)

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
To check if a linked list is a palindrome, we can use the following approach :

- Find the middle of the linked list using the slow and fast pointers technique.
- Reverse the second half of the linked list.
- Compare the first half of the original list with the reversed second half.
# Approach
<!-- Describe your approach to solving the problem. -->
- Initialize two pointers, slow and fast, both pointing to the head of the linked list.
- Traverse the list using the slow and fast pointers, where slow moves one step at a time and fast moves two steps at a time. By the time the fast pointer reaches the end of the list, the slow pointer will be at the middle of the list.
- Reverse the second half of the list starting from the node after the slow pointer. This can be done using a separate helper function to reverse a linked list.
- Traverse both the first and second halves of the list simultaneously and compare the values of the nodes.
- If at any point the values of the nodes don't match, return false; otherwise, if we reach the end of the list, return true.

---
Have a look at the code , still have any confusion then please let me know in the comments ... Keep Solving.:)
# Complexity
- Time complexity : $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$n$ : number of nodes in the list
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
    
  // Function to check if the linked list is a palindrome
  public boolean isPalindrome(ListNode head) {
    // Find the middle of the list
    ListNode middle = findMiddle(head);
    // Reverse the second half of the list
    ListNode reversedSecondHalf = reverseList(middle);
    
    // Initialize pointers for traversal
    ListNode p1 = head;
    ListNode p2 = reversedSecondHalf;
    
    // Traverse both halves and compare values
    while (p1 != null && p2 != null) {
      // If values don't match, the list is not a palindrome
      if (p1.val != p2.val) {
        return false;
      }
      // Move pointers to next nodes
      p1 = p1.next;
      p2 = p2.next;
    }
    
    // If traversal completes without finding a mismatch, list is a palindrome
    return true;
  }
  
  // Function to find the middle of the list using slow and fast pointers
  private ListNode findMiddle(ListNode head) {
    ListNode slow = head;
    ListNode fast = head;
    
    // Move slow pointer by one step and fast pointer by two steps
    while (fast != null && fast.next != null) {
      slow = slow.next;
      fast = fast.next.next;
    }
    
    // Return the middle node
    return slow;
  }
  
  // Function to reverse a linked list
  private ListNode reverseList(ListNode head) {
    ListNode prev = null;
    ListNode current = head;
    
    // Iterate through the list, reversing pointers
    while (current != null) {
      ListNode next = current.next;
      current.next = prev;
      prev = current;
      current = next;
    }
    
    // Return the new head of the reversed list
    return prev;
  }
}
```
