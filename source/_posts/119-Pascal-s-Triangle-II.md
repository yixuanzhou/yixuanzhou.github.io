---
title: 119. Pascal's Triangle II
date: 2018-03-02 23:56:45
tags: LeetCode
categories: LeetCode
---
### Problem Description:
Given an index k, return the kth row of the Pascal's triangle.

### Note
Write code according to the rule of Pascal's Triangles.

### Code
    public List<Integer> getRow(int rowIndex) {
        List<Integer> curr = new ArrayList<>();
        curr.add(1);
        for (int i = 0; i < rowIndex; i++) {
            List<Integer> next = new ArrayList<>();
            next.add(1);
            for (int j = 0; j < curr.size()-1; j++) {
                next.add(curr.get(j)+curr.get(j+1));
            }
            next.add(1);
            curr = next;
        }
        return curr;
    }