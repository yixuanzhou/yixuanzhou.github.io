---
title: 6. ZigZag Conversion
date: 2018-03-18 21:26:11
tags: LeetCode
categories: LeetCode
---
### Problem Description:
The string **"PAYPALISHIRING"** is written in a zigzag pattern on a given number of rows like this: (you may want to display this pattern in a fixed font for better legibility)

    P   A   H   N
    A P L S I I G
    Y   I   R
And then read line by line: **"PAHNAPLSIIGYIR"**

Write the code that will take a string and make this conversion given a number of rows:

    string convert(string text, int nRows);
**convert("PAYPALISHIRING", 3)** should return **"PAHNAPLSIIGYIR"**.

### Note
An intuitively way to do this is to construct nRows of strings, and add char to each string according to the zigzag order. We can use StringBuilder because it is much faster than string concatenation.

### Code
    public String convert(String s, int numRows) {
        StringBuilder zigzag = new StringBuilder();
        StringBuilder[] sbarray = new StringBuilder[numRows];
        for(int i = 0; i < numRows; i++){
            sbarray[i] = new StringBuilder("");
        }
        int i = 0;
        while (i < s.length()) {
            for (int j = 0; j < numRows; j++) {
                if (i >= s.length()) { break; }
                sbarray[j].append(s.charAt(i++));
            }

            for (int k = numRows-2; k > 0; k--) {
                if (i >= s.length()) { break; }
                sbarray[k].append(s.charAt(i++));
            }
        }

        for (StringBuilder sb : sbarray) {
            zigzag.append(sb.toString());
        }

        return zigzag.toString();
    }
