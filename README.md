# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Always here to assist you guys.

## Today's 12-03-24 

## [1171. Remove Zero Sum Consecutive Nodes from Linked List](https://leetcode.com/problems/remove-zero-sum-consecutive-nodes-from-linked-list/description/?envType=daily-question&envId=2024-03-12)

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
The goal of my algorithm should be to remove zero-sum sublists from a given linked list. 

# Approach
<!-- Describe your approach to solving the problem. -->
My approach involved using a dummy node and a HashMap to keep track of the prefix sum and the corresponding nodes.

**Initialization :**
- Created a dummy node with a value of 0 and set it as the head.
- Initialized a HashMap to store the prefix sum and corresponding nodes, starting with a prefix sum of 0 pointing to the dummy node.
- Set the initial prefix sum variable to 0.

**Populated the HashMap :**
- Traversed the linked list, updating the prefix sum as we iterate.
- Stored the current prefix sum and the corresponding node in the HashMap.

**Removed Zero-Sum Sublists :**
- Reset the prefix sum variable to 0.
- Traversed the linked list again.
- Updated the next pointers of nodes to remove zero-sum sublists by pointing them to the next node after the corresponding prefix sum in the HashMap.

**Result  :**
- Returned the modified list starting from the dummy node's next.

My approach efficiently handled the removal of zero-sum sublists by leveraging the HashMap to keep track of the prefix sums and their corresponding nodes.

---
Have a look at the code , still have any confusion then please let me know in the comments ... Keep Solving.:)
# Complexity
- Time complexity : $O(N)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$N$ : number of nodes in the linked list
- Space complexity : $O(N)$
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
    
    // Static variables to store the map, the current node, and the prefix sum
    static Map<Integer, ListNode> m;
    static ListNode t;
    static int prefixJor;

    // Function to remove zero-sum sublists
    public ListNode removeZeroSumSublists(ListNode head) {
        
        // Creating a dummy node with value 0 and set it as the head
        t = new ListNode(0, head);
        
        // Initializing the map with prefix sum 0 pointing to the dummy node
        m = new HashMap<>();
        m.put(0, t);
        
        // Initializing the prefix sum variable
        prefixJor = 0;
        
        // Populating the map with prefix sum and corresponding nodes
        for (ListNode node = t; node != null; node = node.next) {
            prefixJor += node.val;
            m.put(prefixJor, node);
        }
        
        // Resetting prefix sum
        prefixJor = 0;
        
        // Updating the next pointers to remove zero-sum sublists
        for (ListNode node = t; node != null; node = node.next) {
            prefixJor += node.val;
            node.next = m.get(prefixJor).next;
        }
        
        // Returning the modified list starting from the dummy node's next
        return t.next;
    }
}
```
