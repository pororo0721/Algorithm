# Word Search

>Given an m x n grid of characters board and a string word, return true if word exists in the grid. The word can be constructed from letters of sequentially adjacent cells, where adjacent cells are horizontally or vertically neighboring. The same letter cell may not be used more than once.


-  Example 1:
Input: board = [["A","B","C","E"],["S","F","C","S"],["A","D","E","E"]], word = "ABCCED"
Output: true

- Example 2: 
Input: board = [["A","B","C","E"],["S","F","C","S"],["A","D","E","E"]], word = "SEE"
Output: true

- Example 3: 
Input: board = [["A","B","C","E"],["S","F","C","S"],["A","D","E","E"]], word = "ABCB"
Output: false

## 제한사항
- m x n 의 크기의 문자 2차원 배열
- 1 <=m <=200~300, 1 <=n<=200~300
- word의 길이는, 1 <=len(word) <=10^3~10^4



## 아이디어 

| |아이디어1(Brute-Force) |
|----------------|-------------------------------|
|1 |board 배열의 모든 요소를 순회한다.|
|2 |word[0]과 board[x][y]요소가 같다면, |
|  |`x,y위치의 문자와 word의 현재 문자와 같은지 확인`|
|  |`x,y가 board 크기를 벗어나는지 확인` |
|  |`이미 방문한 위치인지 확인`|
|  |`board[x-1][y]와 word의 다음 문자로 재귀 호출`|
|  |`board[x+1][y]와 word의 다음 문자로 재귀 호출`|
|  |`board[x][y-1]와 word의 다음 문자로 재귀 호출`|
|  |`board[x][y+1]와 word의 다음 문자로 재귀 호출`|
|시간 복잡도|O(m*n*4^L) m*n은 board의 크기, L은 입력 문자열의 길이|
|공간 복잡도|O(1) |



### 아이디어1(Bit Manipulation)

```
class Solution:
    def exist(self, board: List[List[str]], word: str) -> bool:
        direction =[[-1,0],[1,0],[0,-1],[0,1]]
        
        def search_direction(x:int, y:int, subword:str):
            if(x<0 or x >= len(board)) or (y <0 or y >= len(board[0])):
                return False
            
            if board[x][y] != subword[0]:
                return False
            
            if len(subword) == 1:
                return True
            
            board[x][y] ='.'
            
            for i, j in direction:
                if search_direction(x+i, y+j, subword[1:]):
                    return True
                
            
            board[x][y] = subword[0]
            return False
        
        res = False
        for x in range(len(board)):
            for y in range(len(board[0])):
                if board[x][y] == word[0] and search_direction(x,y, word):
                    res= True
                    break
        return res        

```