---
title: 118. Pascal's Triangle
date: 2018-03-02 23:47:36
tags: LeetCode
categories: LeetCode
---
### Problem Description:
Given numRows, generate the first numRows of Pascal's triangle.

### Note
Write code according to the rule of Pascal's Triangles.

### Code
    public List<List<Integer>> generate(int numRows) {
        List<List<Integer>> pascalTriangle = new ArrayList<>();
        if (numRows == 0) { return pascalTriangle; }
        List<Integer> curr = new ArrayList<>();
        curr.add(1);
        pascalTriangle.add(curr);
        for (int i = 1; i < numRows; i++) {
            List<Integer> next = new ArrayList<>();
            next.add(1);
            for (int j = 0; j < curr.size()-1; j++) {
                next.add(curr.get(j)+curr.get(j+1));
            }
            next.add(1);
            curr = next;
            pascalTriangle.add(curr);
        }
        return pascalTriangle;
    }
