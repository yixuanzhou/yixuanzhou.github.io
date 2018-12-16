---
title: 2. Add Two Numbers
date: 2018-03-18 06:26:03
tags: LeetCode
categories: LeetCode
---
### Problem Description:
You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

    Example
    Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)
    Output: 7 -> 0 -> 8
    Explanation: 342 + 465 = 807.

### Note
This is basically a sum of digit problem, we can do it by traverse these two linked lists, and sum the value of each ListNode sum. Then take the sum as the new ListNode of the result. Make sure that the carry is included. And note that if there is a carry when the traversal is over, don't forget to add a new ListNode to the head.

### Code
	public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode sum = new ListNode(0);
        ListNode result = sum;
        int carry = 0;
        int v1, v2;
        int currdigit;
        while (l1 != null || l2 != null) {
            if (l1 != null) {
                v1 = l1.val;
                l1 = l1.next;
            } else {
                v1 = 0;
            }
            if (l2 != null) {
                v2 = l2.val;
                l2 = l2.next;
            } else {
                v2 = 0;
            }
            currdigit = v1 + v2 + carry;
            sum.next = new ListNode(currdigit % 10);
            carry = currdigit > 9 ? 1 : 0;
            sum = sum.next;
        }
        if (carry == 1) {
            sum.next = new ListNode(1);
        }
        return result.next;
    }