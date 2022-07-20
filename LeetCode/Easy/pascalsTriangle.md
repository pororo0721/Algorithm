# Pascal's Triangle

>Given an integer numRows, return the first numRows of Pascal's triangle.In Pascal's triangle, each number is the sum of the two numbers directly above it as shown:

https://upload.wikimedia.org/wikipedia/commons/0/0d/PascalTriangleAnimated2.gif

-  Example 1:
Input: numRows = 5
Output: [[1],[1,1],[1,2,1],[1,3,3,1],[1,4,6,4,1]]

- Example 2: 
Input: numRows = 1
Output: [[1]]



## 제한사항
- 입력값은 양의 정수
- 반환값은 2차원 배열 혹은 리스트


## 아이디어 

|                |아이디어1(Brute-Force)          |
|----------------|-------------------------------|
|1 |기반 리스트 생성 |    
|2 |1번째 리스트 요소를 1로 초기화 한다.|
|3 |입력으로 주어진 행수(numRows)만큼 순회한다. | 
|  |`항상 행의 맨 앞과 맨 뒤의 값은 1이다.` |
|  |`순회하면서 해당 줄(line)을 생성하기 위해서는 이전행의 값을 참조하여 더하거나 그대로 사용한다` |
|시간 복잡도| O(N^2)|
|공간 복잡도| O(1)|


### 아이디어1(Brute-Force)

```
class Solution:
    def generate(self, numRows: int) -> List[List[int]]:
        pascal =[]

        if numRows <=0:
            return pascal

        pascal.append([1])

        for i in range(1, numRows):
            prev_len = len(pascal[i-1])
            curr_list=[]

            for j in range(prev_len+1):
                num=1
                if j !=0 and j != prev_len:
                    num= pascal[i-1][j-1]+pascal[i-1][j]

                curr_list.append(num)

            pascal.append(curr_list)

        return pascal                


```
