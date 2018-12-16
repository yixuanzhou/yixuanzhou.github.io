---
title: 108. Convert Sorted Array to Binary Search Tree
date: 2018-02-28 09:13:39
tags: LeetCode
categories: LeetCode
---

### Problem Description:
Given an array where elements are sorted in ascending order, convert it to a height balanced BST.

For this problem, a height-balanced binary tree is defined as a binary tree in which the depth of the two subtrees of every node never differ by more than 1.

### Note
We can use dichotomy method to solve this problem. Since it's a sorted array, the mid-point of the array is also the mid-value of the array. So we can use the mid-point as the root of each subtree. And for the first half of the array, make it as the left subtree, the second half as the right subtree. And do it recursively.

### Code
    public TreeNode sortedArrayToBST(int[] nums) {
        if (nums.length == 0) { return null; }
        if (nums.length == 1) { return new TreeNode(nums[0]); }
        
        TreeNode root = new TreeNode(nums[nums.length/2]);
        root.left = sortedArrayToBST(Arrays.copyOfRange(nums, 0, nums.length/2));
        root.right = sortedArrayToBST(Arrays.copyOfRange(nums, nums.length/2+1, nums.length));
            
        return root;
    }
