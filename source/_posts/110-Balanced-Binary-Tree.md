---
title: 110. Balanced Binary Tree
date: 2018-03-01 09:30:24
tags: LeetCode
categories: LeetCode
---

### Problem Description:
Given a binary tree, determine if it is height-balanced.

For this problem, a height-balanced binary tree is defined as:

    a binary tree in which the depth of the two subtrees of every node never differ by more than 1.

### Note
For this problem, we can calculate and compare the depth of two subtrees of every nodes.

### Code
    public boolean isBalanced(TreeNode root) {
        if (root == null) { return true;}
        if (root.left == null && root.right == null) { return true; }        
        if (Math.abs(calcDepth(root.left) - calcDepth(root.right)) > 1) { return false; }        
        return isBalanced(root.left) && isBalanced(root.right);             
    }
    
    private int calcDepth(TreeNode root) {
        if (root == null) { return 0; }
        if (root.left == null && root.right == null) { return 1; }
        return 1 + Math.max(calcDepth(root.left), calcDepth(root.right));
    }
