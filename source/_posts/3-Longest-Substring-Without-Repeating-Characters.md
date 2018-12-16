---
title: 3. Longest Substring Without Repeating Characters
date: 2018-03-18 06:43:33
tags: LeetCode
categories: LeetCode
---
### Problem Description:
Given a string, find the length of the longest substring without repeating characters.

    Examples:
    Given "abcabcbb", the answer is "abc", which the length is 3.
    Given "bbbbb", the answer is "b", with the length of 1.
    Given "pwwkew", the answer is "wke", with the length of 3. Note that the answer must be a substring, "pwke" is a subsequence and not a substring.

### Note
For each char of string, count how many different chars subsequently it has. And return the maximum count.

### Code
	public int lengthOfLongestSubstring(String s) {
        int max_len = 0;
        if (s.length() == 1) { return 1; }
        for (int i = 0; i < s.length(); i++) {
            String curr = "" + s.charAt(i);
            int curr_len = 1;
            for (int j = i+1; j < s.length(); j++) {
                if (curr.indexOf(s.charAt(j)) >= 0) {
                    max_len = curr_len > max_len ? curr_len : max_len;
                    break;
                } else {
                    curr = s.substring(i,j+1);
                    if (++curr_len > max_len) { max_len = curr_len; }
                }
            }
        }
        return max_len;
    }
