---
title: 125. Valid Palindrome
date: 2018-03-03 16:14:37
tags: LeetCode
categories: LeetCode
---
### Problem Description:
Given a string, determine if it is a palindrome, considering only alphanumeric characters and ignoring cases.

For example,
"A man, a plan, a canal: Panama" is a palindrome.
"race a car" is not a palindrome.

Note:
Have you consider that the string might be empty? This is a good question to ask during an interview.

For the purpose of this problem, we define empty string as valid palindrome.

### Note
It's a typical two-pointer problem, just remember to check out whether the character is a letter or a digit.

### Code
    public boolean isPalindrome(String s) {
        if (s.length() == 0) { return true; }
        s = s.toLowerCase();
        int head = 0;
        int tail = s.length()-1;
        while (head <= tail) {
            char chHead = s.charAt(head);
            char chTail = s.charAt(tail);
            if (!Character.isLetterOrDigit(chHead)) { head++; continue; }
            if (!Character.isLetterOrDigit(chTail)) { tail--; continue; }
            if (Character.isLetterOrDigit(chHead) && Character.isLetterOrDigit(chTail)) {
                if (chHead != chTail) { return false; }
                head++; tail--;
            }
        }
        return true;
    }

