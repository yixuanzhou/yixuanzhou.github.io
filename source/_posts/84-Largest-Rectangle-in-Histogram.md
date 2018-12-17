---
title: 84. Largest Rectangle in Histogram
date: 2018-12-16 18:44:47
tags: LeetCode
categories: LeetCode
---

### Problem Description:
Given n non-negative integers representing the histogram's bar height where the width of each bar is 1, find the area of largest rectangle in the histogram.

For example, given a histogram where width of each bar is 1, given height = [2,1,5,6,2,3]. The largest rectangle is shown in the shaded area, which has area = 10 unit.

![alt text](https://assets.leetcode.com/uploads/2018/10/12/histogram_area.png)

Input: [2,1,5,6,2,3]

Output: 10

### Note
This problem can be solved using stack. The stack stores the index of heights. At ith iteration, if heights[i] is bigger or equal to heights[top of stack], push index i into stack. On the other hand, if heights[i] is smaller than heights[top of stack], we know that the maximum area must happen before index i.

Now on the top of stack gives is the index of the biggest height till index i. And the width is directly derived from stack.

This solution comes from [GeekforGeeks](https://www.geeksforgeeks.org/largest-rectangle-under-histogram/).

Complexity: O(n).

### Code
    public int largestRectangleArea(int[] heights) {
        if (heights == null || heights.length == 0) return 0;
        Stack<Integer> s = new Stack<>();
        int maxArea = 0;
        for (int i = 0; i <= heights.length; i++) {
            int h1 = i == heights.length ? 0 : heights[i];
            if (s.isEmpty() || h1 >= heights[s.peek()]) s.push(i);
            else {
                int h = heights[s.pop()];
                int w = s.isEmpty() ? i : i-s.peek()-1;
                maxArea = Math.max(maxArea, w*h);
                i--;
            }
        }
        return maxArea;
    }
