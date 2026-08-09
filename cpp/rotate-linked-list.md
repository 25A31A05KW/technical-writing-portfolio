# technical-writing-portfolio
My technical writing and software documentation portfolio

# Rotate Linked List — C++

## Introduction

A linked list is a linear data structure where each node contains a value and a pointer to the next node.

## Problem Statement

Given a singly linked list, rotate the list to the right by `k` positions.

## Example

Input:

1 → 2 → 3 → 4 → 5

k = 2

Output:

4 → 5 → 1 → 2 → 3

## Approach

The list can be rotated by moving the last node to the beginning.

For an efficient solution, we first find the length of the linked list and reduce `k` using the length of the list.

## C++ Implementation

```cpp
class Solution {
public:
    ListNode* rotateRight(ListNode* head, int k) {
        if (head == NULL || head->next == NULL || k == 0)
            return head;

        int n = 1;
        ListNode* tail = head;

        while (tail->next != NULL) {
            tail = tail->next;
            n++;
        }

        k = k % n;

        if (k == 0)
            return head;

        tail->next = head;

        int steps = n - k;
        ListNode* newTail = head;

        for (int i = 1; i < steps; i++) {
            newTail = newTail->next;
        }

        ListNode* newHead = newTail->next;
        newTail->next = NULL;

        return newHead;
    }
};
