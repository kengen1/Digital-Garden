## 1. Overview

- Uses two pointers that traverse a sequence at different speeds
- Typically used for problems involving **cyclic detection, finding middle elements, or detecting patterns** in linked lists or arrays

Commonly applied to:
- Detecting cycles in linked lists (Floyd’s Cycle Detection Algorithm).
- Finding the middle of a linked list.
- Solving problems related to runner techniques (fast pointer "laps" slow pointer).

*Key patterns:*
- **Cycle Detection**: The fast pointer moves two steps while the slow pointer moves one step. If they meet, a cycle exists.
- **Finding Middle**: The slow pointer moves one step while the fast pointer moves two steps. When the fast pointer reaches the end, the slow pointer is at the middle.

Advantages:
- works in O(n) time for many problems involving linked lists or sequences
- uses constant extra space since only two pointers are required
- avoids additional data structure like sets or hashtables in cycle detection
## 2. Example Implementation
### Problem: Detect a cycle in a linked list

```cpp
struct ListNode {
    int val;
    ListNode* next;
    ListNode(int x) : val(x), next(nullptr) {}
};

bool hasCycle(ListNode* head) {
    if (!head || !head->next) return false; // Edge case: empty list or single node

    ListNode* slow = head;  // Moves one step
    ListNode* fast = head;  // Moves two steps

    while (fast && fast->next) {
        slow = slow->next;
        fast = fast->next->next;

        if (slow == fast) {  // Cycle detected
            return true;
        }
    }
    return false;  // No cycle found
}

```

