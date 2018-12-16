---
title: 111. Minimum Depth of Binary Tree
date: 2018-03-01 09:36:49
tags: LeetCode
categories: LeetCode
---
### Problem Description:
Given a binary tree, find its minimum depth.

The minimum depth is the number of nodes along the shortest path from the root node down to the nearest leaf node.

### Note
Use a helper function to calculate the depth of each node, and if the node is a leaf, return its depth. Then choose the minimum depth among all leaves.

### Code
    public int minDepth(TreeNode root) {
        if (root == null) { return 0; }
        int depth = 1;
        return minDepthHelper(root, depth);
    }
    
    private int minDepthHelper(TreeNode root, int depth) {
        if (root == null) { return Integer.MAX_VALUE; }
        if (root.left == null && root.right == null) {
            return depth;
        } else {
            return Math.min(minDepthHelper(root.left, ++depth), minDepthHelper(root.right, ++depth));
        }
    }
