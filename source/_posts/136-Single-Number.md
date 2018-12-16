---
title: 136. Single Number
date: 2018-03-03 16:14:52
tags: LeetCode
categories: LeetCode
---

### Problem Description:
Given an array of integers, every element appears twice except for one. Find that single one.

Note:
Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?

### Note
Here is the trick: using bitwise XOR.

For any bit: 0 ^ N = N, N ^ N = 0.

Therefore, if a number appears twice in an array, its bit would be canceled by XOR, and the only bits left would be that single number.

### Code
    public int singleNumber(int[] nums) {
        int ans = 0;
        for (int num : nums) {
            ans ^= num;
        }
        return ans;
    }
