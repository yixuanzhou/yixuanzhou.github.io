---
title: 142. Linked List Cycle II
date: 2018-03-10 17:06:06
tags: LeetCode
categories: LeetCode
---
### Problem Description:
Given a linked list, return the node where the cycle begins. If there is no cycle, return null.

Note: Do not modify the linked list.

Follow up:
Can you solve it without using extra space?

### Note
First, using tortoise & hare algorithm to detect whether it has a cycle in the list.

Next, assume that the length of array is n, and the cycle begins at m. Now suppose that two pointers meets at k. This means that the slower one has walked k steps, and faster one has walked 2k steps.
 
We can safely conclude that n + (k - m) = 2k. => k = n - m. This means that if the slower pointer continues to walk m steps, it would arrive at the point where cycle begins. Not surprisingly, if we set another pointer to walk by one step from head now, it will meet the former slower pointer at the point where cycle begins.

### Code
    public ListNode detectCycle(ListNode head) {
        if (head == null) { return null; }
        ListNode rabbit = head;
        ListNode tortoise = head;
        boolean isCycle = false;
        while (rabbit.next != null && rabbit.next.next != null) {
            rabbit = rabbit.next.next;
            tortoise = tortoise.next;
            if (rabbit == tortoise) { isCycle = true; break; }
        }

        if (!isCycle) {
            return null;
        } else {
            rabbit = head;
            while (rabbit != tortoise) {
                rabbit = rabbit.next;
                tortoise = tortoise.next;
            }
        }
        return rabbit;
    }