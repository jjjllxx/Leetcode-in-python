# 733. Flood Fill
https://leetcode-cn.com/problems/flood-fill  
An image is represented by an m x n integer grid image where image[i][j] represents the pixel value of the image.  

You are also given three integers sr, sc, and newColor. You should perform a flood fill on the image starting from the pixel image[sr][sc]. 

To perform a flood fill, consider the starting pixel, plus any pixels connected 4-directionally to the starting pixel of the same color as the starting pixel, plus any pixels connected 4-directionally to those pixels (also with the same color), and so on. Replace the color of all of the aforementioned pixels with newColor.

Return the modified image after performing the flood fill.  

 

Example 1:

<img width="562" alt="image" src="https://user-images.githubusercontent.com/60777462/152635229-3626a22f-27b4-4d7b-b4f6-1af0fbb19aa2.png">  

Input: image = [[1,1,1],[1,1,0],[1,0,1]], sr = 1, sc = 1, newColor = 2   
Output: [[2,2,2],[2,2,0],[2,0,1]]  
Explanation: From the center of the image with position (sr, sc) = (1, 1) (i.e., the red pixel), all pixels connected by a path of the same color as the starting pixel (i.e., the blue pixels) are colored with the new color.  
Note the bottom corner is not colored 2, because it is not 4-directionally connected to the starting pixel.  

Example 2:  
Input: image = [[0,0,0],[0,0,0]], sr = 0, sc = 0, newColor = 2  
Output: [[2,2,2],[2,2,2]]  

Constraints:  
m == image.length  
n == image[i].length  
1 <= m, n <= 50  
0 <= image[i][j], newColor < 216  
0 <= sr < m  
0 <= sc < n  

## BFS  
``` python3
class Solution:
    def floodFill(self, image: List[List[int]], sr: int, sc: int, newColor: int) -> List[List[int]]:
        target=image[sr][sc]
        if target==newColor:
            return image
        bfs=collections.deque([(sr,sc)])
        row,col=len(image),len(image[0])
        image[sr][sc]=newColor
        while bfs:
            x,y=bfs.popleft()
            for mx,my in [(x-1,y),(x+1,y),(x,y-1),(x,y+1)]:
                if 0<=mx<row and 0<=my<col and image[mx][my]==target:
                    bfs.append((mx,my))
                    image[mx][my]=newColor
        return image
```

## DFS  
``` python3
class Solution:
    def floodFill(self, image: List[List[int]], sr: int, sc: int, newColor: int) -> List[List[int]]:
        row,col=len(image),len(image[0])
        target=image[sr][sc]
        def dfs(x,y):
            if image[x][y]==target:
                image[x][y]=newColor
                for mx,my in [(x-1,y),(x+1,y),(x,y-1),(x,y+1)]:
                    if 0<= mx <row and 0<=my<col and image[mx][my]==target:
                        dfs(mx,my)
        if target!=newColor:
            dfs(sr,sc)
        return image
```
