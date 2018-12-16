---
title: 88. Merge Sorted Array
date: 2018-02-14 10:23:46
tags: LeetCode
categories: LeetCode
---

### Problem Description:
Given two sorted integer arrays nums1 and nums2, merge nums2 into nums1 as one sorted array.

Note:
    
You may assume that nums1 has enough space (size that is greater or equal to m + n) to hold additional elements from nums2. The number of elements initialized in nums1 and nums2 are m and n respectively.


### Note
Since nums1 has enough space to hold all elements, we may assume that the length of nums1 is **m + n - 1**. Then we can iteratively compare two arrays and add bigger element into nums1 from back to front. In case that there are remaining elements in nums2 (which means the remaining elements are all smaller than the smallest element in nums1), we also have to add the remaining elements into the nums1.

### Code
    public void merge(int[] nums1, int m, int[] nums2, int n) {
    
        int i = m - 1;
        int j = n - 1;
        int k = m + n - 1;
        while (i >= 0 && j >= 0) {
            nums1[k--] = nums1[i] > nums2[j] ? nums1[i--] : nums2[j--];
        }
        while (j >= 0) {
            nums1[j] = nums2[j--];
        }
     }
