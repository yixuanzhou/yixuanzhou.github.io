---
title: 112. Path Sum
date: 2018-03-02 23:29:42
tags: LeetCode
categories: LeetCode
---
### Problem Description:
Given a binary tree and a sum, determine if the tree has a root-to-leaf path such that adding up all the values along the path equals the given sum.

### Note
Keep in mind that it's a root-to-**leaf** path.

### Code
    public boolean hasPathSum(TreeNode root, int sum) {
        if (root == null) { return false; }
        if (root.left == null && root.right == null) {
            if (sum-root.val == 0) { return true; }
        }
        return hasPathSum(root.left, sum-root.val) || hasPathSum(root.right, sum-root.val);
    }
