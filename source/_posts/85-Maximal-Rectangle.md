---
title: 85. Maximal Rectangle
date: 2018-12-16 21:27:17
tags: LeetCode
categories: LeetCode
---

### Problem Description:
Given a 2D binary matrix filled with 0's and 1's, find the largest rectangle containing only 1's and return its area.

Example:

    Input:  
    [  
      ["1","0","1","0","0"],  
      ["1","0","1","1","1"],  
      ["1","1","1","1","1"],  
      ["1","0","0","1","0"]  
    ]  
    Output: 6


### Note
This problem can be transformed into LC84 (Largest Rectangle in Histogram). So we iterate through all rows in matrix, and we count the number of continuous 1s in each column from the current row till the top. This would result in a histogram. Then we can calculate the area using that histogram ([LC84](https://yixuanzhou.github.io/2018/12/16/84-Largest-Rectangle-in-Histogram/)).

Complexity: O(n^2).

### Code
    public int maximalRectangle(char[][] matrix) {
        if (matrix.length == 0) return 0;
        int[] hist = new int[matrix[0].length];
        int maxArea = 0;

        for (int i = 0; i < matrix.length; i++) {
            char[] curr = matrix[i];
            for (int j = 0; j < curr.length; j++) {
                if (curr[j] == '1') hist[j] += 1;
                else hist[j] = 0;
            }            
            maxArea = Math.max(maxArea, calculateArea(hist));
        }

        return maxArea;        
    }

    private int calculateArea(int[] heights) {
        int area = 0;
        Stack<Integer> stack = new Stack<>();

        for (int i = 0; i <= heights.length; i++) {
            int h1 = i == heights.length ? 0 : heights[i];
            if (stack.isEmpty() || h1 >= heights[stack.peek()]) stack.push(i);
            else {
                int h = heights[stack.pop()];
                int w = stack.isEmpty() ? i : i-stack.peek()-1;
                area = Math.max(area, w*h);
                i--;
            }
        }

        return area;
    }
