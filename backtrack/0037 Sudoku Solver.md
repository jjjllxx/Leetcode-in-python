# 37. Sudoku Solver
https://leetcode-cn.com/problems/sudoku-solver  
Write a program to solve a Sudoku puzzle by filling the empty cells.  
A sudoku solution must satisfy all of the following rules:  
Each of the digits 1-9 must occur exactly once in each row.  
Each of the digits 1-9 must occur exactly once in each column.  
Each of the digits 1-9 must occur exactly once in each of the 9 3x3 sub-boxes of the grid.  
The '.' character indicates empty cells.  

Example 1:  
![image](https://user-images.githubusercontent.com/60777462/153570025-fbb57859-b6b1-455f-90cc-2ff46786dbe6.png)  
Input: board = [  
["5","3",".",".","7",".",".",".","."],  
["6",".",".","1","9","5",".",".","."],  
[".","9","8",".",".",".",".","6","."],  
["8",".",".",".","6",".",".",".","3"],  
["4",".",".","8",".","3",".",".","1"],  
["7",".",".",".","2",".",".",".","6"],  
[".","6",".",".",".",".","2","8","."],  
[".",".",".","4","1","9",".",".","5"],  
[".",".",".",".","8",".",".","7","9"]]  
Output: [  
["5","3","4","6","7","8","9","1","2"],  
["6","7","2","1","9","5","3","4","8"],  
["1","9","8","3","4","2","5","6","7"],  
["8","5","9","7","6","1","4","2","3"],  
["4","2","6","8","5","3","7","9","1"],  
["7","1","3","9","2","4","8","5","6"],  
["9","6","1","5","3","7","2","8","4"],  
["2","8","7","4","1","9","6","3","5"],  
["3","4","5","2","8","6","1","7","9"]]  
Explanation: The input board is shown above and the only valid solution is shown below:  
![image](https://user-images.githubusercontent.com/60777462/153570065-408c5832-3349-4926-a97d-3b7219bec212.png)  

Constraints:
board.length == 9
board[i].length == 9
board[i][j] is a digit or '.'.
It is guaranteed that the input board has only one solution.

``` python3
class Solution:
    def solveSudoku(self, board: List[List[str]]) -> None:
        """
        Do not return anything, modify board in-place instead.
        """
        def filling(start):
            nonlocal flag
            if start == len(unfilled):
                flag = True
                return
            i,j=unfilled[start]
            for digit in range(9):
                if col[i][digit]==row[j][digit]==block[i//3][j//3][digit]==False:
                    col[i][digit]=row[j][digit]=block[i//3][j//3][digit]=True
                    board[i][j]=str(digit+1)
                    filling(start+1)
                    col[i][digit]=row[j][digit]=block[i//3][j//3][digit]=False
                if flag:
                    return

        
        col=[[False]*9 for i in range(9)]
        row=[[False]*9 for i in range(9)]
        block=[[[False]*9 for i in range(3)] for j in range(3)]
        flag=False
        unfilled=[]
        for i in range(9):
            for j in range(9):
                if board[i][j]=='.':
                    unfilled.append((i,j))
                else:
                    digit=int(board[i][j])-1
                    col[i][digit]=row[j][digit]=block[i//3][j//3][digit]=True
        filling(0)
        
```
