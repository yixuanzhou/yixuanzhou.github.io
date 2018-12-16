---
title: 67. Add Binary
date: 2018-02-12 16:16:32
tags: LeetCode
categories: LeetCode
---

### Problem Description:
Given two binary strings, return their sum (also a binary string).

For example, a = "11", b = "1", Return "100".

### Note
Not much thing to talk about this problem. Note that an integer should be used to keep track of the carry. Originally I used "result = Integer.toString(sum) + result" to update result，however, Intellij IDE reminds me to use **"StringBuilder"** when updating String in loops. So, that's it.

### Code
    public String addBinary(String a, String b) {
        int la = a.length() - 1; int lb = b.length() - 1; int carry = 0;
        StringBuilder result = new StringBuilder();

        while (la >= 0 || lb >= 0) {
            int sum = carry;            
            if (la >= 0) {sum += a.charAt(la) - '0'; la--;}
            if (lb >= 0) {sum += b.charAt(lb) - '0'; lb--;}
            if (sum > 1) {carry = 1; sum = sum % 2;}
            else {carry = 0;}
            result.insert(0, sum);
        }
        if (carry > 0) {result.insert(0, carry);}
        return result.toString();
    }
