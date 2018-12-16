---
title: 70. Climbing Stairs
date: 2018-02-12 20:36:24
tags: LeetCode
categories: LeetCode
---

### Problem Description:
You are climbing a stair case. It takes n steps to reach to the top.

Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?

Note: Given n will be a positive integer.

### Note
This is a typical Fibonacci problem.

### Code
    public int climbingStairs (int n) {
        if (n == 1) {
            return 1;
        }
        if (n == 2) {
            return 2;
        }
        int step_one = 1;
        int step_two = 2;
        int all_steps = 0;

        for (int i = 2; i < n; i++) {
            all_steps = step_one + step_two;
            step_one = step_two;
            step_two = all_steps;
        }
        return all_steps;
    }
