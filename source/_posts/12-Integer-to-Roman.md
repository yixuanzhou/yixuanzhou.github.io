---
title: 12. Integer to Roman
date: 2018-03-18 21:07:52
tags: LeetCode
categories: LeetCode
---
### Problem Description:
Given an integer, convert it to a roman numeral.

Input is guaranteed to be within the range from 1 to 3999.

### Note
Here is the list of Roman symbols which include subtractive cases:

SYMBOL | VALUE
:---: | :---:
I  | 1
IV | 4
V  | 5
IX | 9
X  | 10
XL | 40
L  | 50
XC | 90
C  | 100
CD | 400
D  | 500
CM | 900
M  | 1000

It's pretty fast to use this table to transfer integer to Roman numerals.
### Code
	public String intToRoman(int num) {
        StringBuilder roman = new StringBuilder("");
        int[] values = {1000,900,500,400,100,90,50,40,10,9,5,4,1};
        String[] symbols = {"M","CM","D","CD","C","XC","L","XL","X","IX","V","IV","I"};
        int q = 0;
        for (int i = 0; i < 13; i++) {
            if (num >= values[i]) {
                q = num / values[i];
                num = num % values[i];
                for (int j = 0; j < q; j++) {
                    roman.append(symbols[i]);
                }
            }
        }
        return roman.toString();
    }
