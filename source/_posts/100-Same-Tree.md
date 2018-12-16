---
title: 100. Same Tree
date: 2018-02-14 10:36:21
tags: LeetCode
categories: LeetCode
---

### Problem Description:
Given two binary trees, write a function to check if they are the same or not.

Two binary trees are considered the same if they are structurally identical and the nodes have the same value.

### Note
Just compare leaves recursively.

### Code
    public boolean isSameTree(TreeNode p, TreeNode q) {
        if (p == null || q == null) { return p == q; }
        if (p.val == q.val) { return isSameTree(p.left, q.left) && isSameTree(p.right, q.right); }
        return false;
    }
