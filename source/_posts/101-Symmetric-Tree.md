---
title: 101. Symmetric Tree
date: 2018-02-23 09:51:01
tags: LeetCode
categories: LeetCode
---

### Problem Description:
Given a binary tree, check whether it is a mirror of itself (ie, symmetric around its center).
### Note
There are two ways to solve this problem: Recursive and Non-Recursive.
 
For the recursive one, we need to recursively compare the left child from the left with the right child from the right, and right child from the left with the left child from the right, since symmetric means symmetric around the center.

For the non-recursive one, the idea is similar to the recursive method, what's different is that I use **stack** this time. The order of push nodes into stack is: left.left, right.right, left.right, right,right. And pop two nodes at a time to compare their value.


### Code
     public boolean isSymmetric(TreeNode root) {
            return root == null || isSymmetricHelp(root.left, root.right);
        }
    
     private boolean isSymmetricHelp(TreeNode left, TreeNode right) {
         if (left == null || right == null) {
             return left == right;
         }
         if (left.val  != right.val) {
             return false;
         } else {
             return isSymmetricHelp(left.right, right.left) && isSymmetricHelp(left.left, right.right);
         }
     }
    
     /* Non-Recursive method */
     public boolean isSymmetricStack(TreeNode root) {
         if (root == null) { return true; }
         Stack<TreeNode> stack = new Stack<>();
         TreeNode left, right;
         if (root.left != null) {
             if (root.right == null) {
                 return false;
             }
             left = root.left;
             right = root.right;
             stack.push(left);
             stack.push(right);
         }
         
             if (root.right != null) {
             if (root.left == null) {
                 return false;
             }
         }
    
         while (!stack.empty()) {
             right = stack.pop();
             left = stack.pop();
             if (left.val != right.val) {
                 return false;
             }
             if (left.left != null) {
                 if (right.right == null) {
                     return false;
                 }
                 stack.push(left.left);
                 stack.push(right.right);
             }
             if (right.right != null) {
                 if (left.left == null) {
                     return false;
                 }
             }
    
                 if (left.right != null) {
                 if (right.left == null) {
                     return false;
                 }
                 stack.push(left.right);
                 stack.push(right.left);
             }
             if (right.left != null) {
                 if (left.right == null) {
                     return false;
                 }
             }
         }    
         return true;
     }
