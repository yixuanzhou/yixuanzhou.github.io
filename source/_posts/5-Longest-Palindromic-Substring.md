---
title: 5. Longest Palindromic Substring
date: 2018-03-18 20:47:18
tags: LeetCode
categories: LeetCode
---
### Problem Description:
Given a string s, find the longest palindromic substring in s. You may assume that the maximum length of s is 1000.

    Example:
    Input: "babad"
    Output: "bab"
Note: "aba" is also a valid answer.


    Example:
    Input: "cbbd"
    Output: "bb"

### Note
There are two kinds of palindrome, one is when the length is odd, the string is odd-symmetry; another is when the length is even, the string is even-symmetry.

### Code
	public String longestPalindrome(String s) {
        if (s.length() <= 1) {
            return s;
        }
        int idx = 0;
        int curr_len = 1;
        for (int i = 1; i < s.length(); i++) {
            if (isPalindrome(s, i-curr_len, i)) {
                curr_len++;
                idx = i;
            }
            if (isPalindrome(s, i-curr_len-1, i)) {
                curr_len += 2;
                idx = i;
            }
        }
        return s.substring(idx-curr_len+1, idx+1);
    }

    private boolean isPalindrome(String s, int start, int end) {
        if (start < 0) { return false; }
        while (start < end) {
            if (s.charAt(start++) != s.charAt(end--)) {
                return false;
            }
        }
        return true;
    }
