---
title: 141. Linked List Cycle
date: 2018-03-10 17:02:59
tags: LeetCode
categories: LeetCode
---
### Problem Description:
Given a linked list, determine if it has a cycle in it.

Follow up:
Can you solve it without using extra space?

### Note
Copied it from the discuss: You can make use of Floyd’s cycle-finding algorithm, also know as tortoise and hare algorithm. The idea is to have two references to the list and move them at different speeds. Move one forward by 1 node and the other by 2 nodes. If the linked list has a loop they will definitely meet.

### Code
    public boolean hasCycle(ListNode head) {
        if (head == null) { return false; }
        ListNode rabbit = head;
        ListNode tortoise = head;
        while (rabbit.next != null && rabbit.next.next != null) {
            rabbit = rabbit.next.next;
            tortoise = tortoise.next;
            if (rabbit == tortoise) { return true; }
        }
        return false;
    }
