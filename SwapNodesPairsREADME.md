# leet-day40

# Problem: Swap Nodes in Pairs

## Description

Given a singly-linked list, you need to swap every two adjacent nodes and return the head of the modified list. The values in the nodes should not be modified; only the nodes themselves can be changed.

## Example

Input: 1 -> 2 -> 3 -> 4
Output: 2 -> 1 -> 4 -> 3

Input: 1 -> 2 -> 3 -> 4 -> 5
Output: 2 -> 1 -> 4 -> 3 -> 5

## Approach

To solve this problem, you can use an iterative approach. Here's how the algorithm works step by step:

1. Check if the linked list is empty or contains only one node. If so, return the list as it is, since there's nothing to swap.
2. Initialize a pointer `newHead` to keep track of the new head of the modified list after swapping.
3. Initialize a `prev` pointer to keep track of the node before the current pair of nodes.
4. Iterate through the linked list while there are at least two nodes left for swapping:
   a. Store the next node of the current pair (i.e., `head->next->next`) in a pointer called `nextNode`.
   b. If `prev` exists, update its `next` pointer to point to the second node of the current pair (`head->next`).
   c. Swap the nodes by updating `head->next->next` to point to the first node of the current pair (`head`).
   d. Update the `head->next` pointer to point to `nextNode`.
   e. Update the `prev` pointer to `head` (current pair is now swapped).
   f. Update `head` to `nextNode` for the next iteration.
5. Return `newHead`, which now points to the new head of the modified linked list.

## Complexity Analysis

The time complexity of this approach is O(n), where n is the number of nodes in the linked list, as we iterate through all nodes once. The space complexity is O(1) since we are using only a few pointers to manipulate the nodes.

## Implementation

The solution is implemented in C++ and utilizes the `ListNode` struct provided in the problem description. The `swapPairs` function takes the head of the linked list as input and returns the head of the modified list.

```cpp
// ListNode struct definition

class Solution {
public:
    ListNode* swapPairs(ListNode* head) {
        if (!head || !head->next) {
            return head;
        }
        
        ListNode* newHead = head->next;
        ListNode* prev = nullptr;
        
        while (head && head->next) {
            ListNode* nextNode = head->next->next;
            
            if (prev) {
                prev->next = head->next;
            }
            head->next->next = head;
            head->next = nextNode;
            
            prev = head;
            head = nextNode;
        }
        
        return newHead;
    }
};
```

## Conclusion

This README file explains the problem statement, approach, complexity analysis, and provides a complete C++ implementation for solving the "Swap Nodes in Pairs" problem.
