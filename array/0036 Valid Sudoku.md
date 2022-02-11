# 36. Valid Sudoku
https://leetcode-cn.com/problems/valid-sudoku  
Determine if a 9 x 9 Sudoku board is valid. Only the filled cells need to be validated according to the following rules:  

Each row must contain the digits 1-9 without repetition.  
Each column must contain the digits 1-9 without repetition.  
Each of the nine 3 x 3 sub-boxes of the grid must contain the digits 1-9 without repetition.  
Note:  
A Sudoku board (partially filled) could be valid but is not necessarily solvable.  
Only the filled cells need to be validated according to the mentioned rules.  
 

Example 1:  
![image](https://user-images.githubusercontent.com/60777462/153569468-a59b2e7c-971e-4f94-be63-1e60aa3672cf.png)  

Input: board =   
[["5","3",".",".","7",".",".",".","."]  
,["6",".",".","1","9","5",".",".","."]  
,[".","9","8",".",".",".",".","6","."]  
,["8",".",".",".","6",".",".",".","3"]  
,["4",".",".","8",".","3",".",".","1"]  
,["7",".",".",".","2",".",".",".","6"]  
,[".","6",".",".",".",".","2","8","."]  
,[".",".",".","4","1","9",".",".","5"]  
,[".",".",".",".","8",".",".","7","9"]]  
Output: true  

Example 2:  
Input: board =   
[["8","3",".",".","7",".",".",".","."]  
,["6",".",".","1","9","5",".",".","."]  
,[".","9","8",".",".",".",".","6","."]  
,["8",".",".",".","6",".",".",".","3"]  
,["4",".",".","8",".","3",".",".","1"]  
,["7",".",".",".","2",".",".",".","6"]  
,[".","6",".",".",".",".","2","8","."]  
,[".",".",".","4","1","9",".",".","5"]  
,[".",".",".",".","8",".",".","7","9"]]  
Output: false  
Explanation: Same as Example 1, except with the 5 in the top left corner being modified to 8. Since there are two 8's in the top left 3x3 sub-box, it is invalid.  

Constraints:  
board.length == 9  
board[i].length == 9  
board[i][j] is a digit 1-9 or '.'.  

``` python3
class Solution:
    def isValidSudoku(self, board: List[List[str]]) -> bool:
        for i in range(9):
            content=''
            for j in range(9):
                now=board[i][j]
                if now.isdigit():
                    if now in content:
                        return False
                    content+=now

        for i in range(9):
            content=''
            for j in range(9):
                now=board[j][i]
                if now.isdigit():
                    if now in content:
                        return False
                    content+=now

        for i in [1,4,7]:
            for j in [1,4,7]:
                content=''
                for m in range(i-1,i+2):
                    for n in range(j-1,j+2):
                        now=board[m][n]
                        if now.isdigit():
                            if now in content:
                                return False
                            content+=now
        return True

```
