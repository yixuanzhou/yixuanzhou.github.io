---
title: 795. Number of Subarrays with Bounded Maximum
date: 2018-03-16 19:15:24
tags: LeetCode
categories: LeetCode
---
### Problem Description:
We are given an array A of positive integers, and two positive integers L and R (L <= R).

Return the number of (contiguous, non-empty) subarrays such that the value of the maximum array element in that subarray is at least L and at most R.

    Example :
    Input: 
    A = [2, 1, 4, 3]
    L = 2
    R = 3
    Output: 3

Explanation: There are three subarrays that meet the requirements: [2], [2, 1], [3].

### Note
Traverse the array from the head, if the element is between L and R, then count how many both preceding and subsequent elements are between L and R. Say, if there are 1 preceding and 2 subsequent elements satisfy the requirement, we would have totally 1 (the element itself) + 1 * (2 + 1) (subarrays including the preceding element) + 2 (subarrays not including preceding element) = 6 subarrays that satisfy the requirement. 


### Code
    public int numSubarrayBoundedMax(int[] A, int L, int R) {
        int count = 0;
        for (int i = 0; i < A.length; i++) {
            if (A[i] >= L && A[i] <= R) {
                count++;
                int index = i;
                int front = 0;
                int back = 0;
                while (index > 0) {
                    index--;
                    if (A[index] >= L && A[index] <= R) { break; }
                    if (A[index] <= R) {
                        front++;
                    } else {
                        break;
                    }
                }
                index = i;
                while (index < A.length-1) {
                    if (A[++index] <= R) {
                        back++;
                    } else {
                        break;
                    }
                }
                count += front * (back + 1) + back;
            }
        }
        return count;
    }
