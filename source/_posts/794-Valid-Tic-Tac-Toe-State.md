---
title: 794. Valid Tic-Tac-Toe State
date: 2018-03-16 20:03:41
tags: LeetCode
categories: LeetCode
---
### Problem Description:
A Tic-Tac-Toe board is given as a string array board. Return True if and only if it is possible to reach this board position during the course of a valid tic-tac-toe game.

The board is a 3 x 3 array, and consists of characters " ", "X", and "O".  The " " character represents an empty square.

Here are the rules of Tic-Tac-Toe:

- Players take turns placing characters into empty squares (" ").
- The first player always places "X" characters, while the second player always places "O" characters.
- "X" and "O" characters are always placed into empty squares, never filled ones.
- The game ends when there are 3 of the same (non-empty) character filling any row, column, or diagonal.
- The game also ends if all squares are non-empty.
- No more moves can be played if the game is over.


    Example 1:
    Input: board = ["O  ", "   ", "   "]
    Output: false
Explanation: The first player always plays "X".

    Example 2:
    Input: board = ["XOX", " X ", "   "]
    Output: false
Explanation: Players take turns making moves.

    Example 3:
    Input: board = ["XXX", "   ", "OOO"]
    Output: false


    Example 4:
    Input: board = ["XOX", "O O", "XOX"]
    Output: true
    
### Note
To Code as playing the Tic-Tac-Toe.

### Code
    public boolean validTicTacToe(String[] board) {
        int player1 = 0;
        int player2 = 0;
        for (int i = 0; i < 3; i++) {
            for (int j = 0; j < 3; j++) {
                if (board[i].charAt(j) == 'X') { player1++; }
                if (board[i].charAt(j) == 'O') { player2++; }
            }
        }
        if (player1 < player2) { return false; }
        if (player1 - player2 > 1) { return false; }

        for (int m = 0; m < 3; m++) {
            if (board[m].equals("XXX")) {
                if (player1 != player2 + 1) { return false; }
            }
            if (board[m].equals("OOO")) {
                if (player2 != player1) { return false; }
            }
            if (board[0].charAt(m) == 'X' && board[1].charAt(m) == 'X' && board[2].charAt(m) == 'X') {
                if (player1 != player2 + 1) { return false; }
            }
            if (board[0].charAt(m) == 'O' && board[1].charAt(m) == 'O' && board[2].charAt(m) == 'O') {
                if (player2 != player1) { return false; }
            }
        }
        if (board[0].charAt(0) == 'X' && board[1].charAt(1) == 'X' && board[2].charAt(2) == 'X') {
            if (player1 != player2 + 1) { return false; }
        }
        if (board[0].charAt(0) == 'O' && board[1].charAt(1) == 'O' && board[2].charAt(2) == 'O') {
            if (player2 != player1) { return false; }
        }
        if (board[0].charAt(2) == 'X' && board[1].charAt(1) == 'X' && board[2].charAt(0) == 'X') {
            if (player1 != player2 + 1) { return false; }
        }
        if (board[0].charAt(2) == 'O' && board[1].charAt(1) == 'O' && board[2].charAt(0) == 'O') {
            if (player2 != player1) { return false; }
        }
        return true;
    }


