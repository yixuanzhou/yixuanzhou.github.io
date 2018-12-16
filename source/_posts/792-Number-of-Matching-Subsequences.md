---
title: 792. Number of Matching Subsequences
date: 2018-03-16 19:42:36
tags: LeetCode
categories: LeetCode
---
### Problem Description:
Given string S and a dictionary of words words, find the number of words[i] that is a subsequence of S.

    Example :
    Input: 
    S = "abcde"
    words = ["a", "bb", "acd", "ace"]
    Output: 3

Explanation: There are three words in words that are a subsequence of S: "a", "acd", "ace".

### Note
Compare each character of the word to the characters of given S. If match, compare next character with position + 1.

### Code
    public int numMatchingSubseq(String S, String[] words) {
        int count = 0;
        for (String word : words) {
            int j = 0;
            boolean found = false;
            for (int i = 0; i < word.length(); i++) {
                char curr = word.charAt(i);
                found = false;
                while (j < S.length()) {
                    if (curr == S.charAt(j)) {
                        j++;
                        found = true;
                        break;
                    }
                    j++;
                }
            }
            if (found) { count++; }
        }
        return count;
    }