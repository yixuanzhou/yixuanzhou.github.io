---
title: 69. Sqrt(x)
date: 2018-02-12 18:49:54
tags: LeetCode
categories: LeetCode
---

### Problem Description:
Implement int sqrt(int x).

Compute and return the square root of x.

x is guaranteed to be a non-negative integer.

### Note
A big obstacle of this problem is to deal with the integer overflow. I mean, the result of integer operation should not exceed the maximum value of Java (-2,147,483,648 ~ 2,147,483,647). For example, to get a mid-point, we typically calculate the half of the left plus right. However, if left plus right exceeds the maximum integer of Java, which would result in troubles. To avoid this, we can use methods like **"mid = left + (right - left) / 2"** and **"mid > x / mid"**.

### Code
    public int sqrt_x(int x) {
        if (x == 0 || x == 1) {
            return x;
        }
    	int left = 0;
    	int right = x;
    	int mid;
    	while (true) {
    	    mid = left + (right - left) / 2;  // avoid overflow
    	    if (mid > x / mid) {  // avoid overflow
    	        right = mid;
            }
            else if (mid * mid == x) {
    	        return mid;
            }
            else {
    	        if ((mid + 1) > x / (mid + 1)) { return mid; }
    	        left = mid;
            }
        }
    }
