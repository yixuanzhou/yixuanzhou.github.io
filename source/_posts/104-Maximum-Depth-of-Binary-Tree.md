---
title: 104. Maximum Depth of Binary Tree
date: 2018-02-25 23:20:12
tags: LeetCode
categories: LeetCode
---

### Problem Description:
Given a binary tree, find its maximum depth.

The maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.
### Note
Do it recursively.

### Code
     public int maxDepth(TreeNode root) {
        if (root == null) {
            return 0;
        }
        return 1 + Math.max(maxDepth(root.left), maxDepth(root.right));
    }
