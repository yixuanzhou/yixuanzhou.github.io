---
title: 83. Remove Duplicates from Sorted List
date: 2018-02-13 17:23:12
tags: LeetCode
categories: LeetCode
---

### Problem Description:
Given a sorted linked list, delete all duplicates such that each element appear only once.

For example,

Given 1->1->2, return 1->2.

Given 1->1->2->3->3, return 1->2->3.

### Note
Create a new ListNode instance, and iteratively scan the original ListNode to add unique Node into the new ListNode. Also, be sure to use a pointer to point at the head of the new ListNode so to return the full ListNodes.

### Code
    public ListNode deleteDuplicates(ListNode head) {
            if (head == null) {
                return null;
            }
            int last = head.val;
            ListNode r = new ListNode(last);
            ListNode result = r;
            int curr;
            while (head.next != null) {       
                head = head.next;
                curr = head.val;
                
                if (curr != last) {
                    last = curr;
                    r.next = new ListNode(curr);
                    r = r.next;
                } else {
                    continue;
                }
                
            }
            return result;            
        }
