# Subsets

>Given an integer array nums of unique elements, return all possible subsets (the power set). The solution set must not contain duplicate subsets. Return the solution in any order.


-  Example 1:
Input: nums = [1,2,3]
Output: [[],[1],[2],[1,2],[3],[1,3],[2,3],[1,2,3]]

- Example 2: 
Input: nums = [0]
Output: [[],[0]]

## 제한사항
- 정수형 배열
- 반환값은 2차원 정수형 배열
- 입력 배열 요소는 중복된 값을 허용하지 않음



## 아이디어 

| |아이디어1(Bit Manipulation) |
|----------------|-------------------------------|
|1 |nth_bit 변수의 목적은 nums 배열에 요소가 3개라면 처음 0일때 비트가000으로 표현되어 비어 있는 부분 집합을 만들어야 하는데 bin(0)은 '0b0'값으로 의도하는 다르게 동작할 수 있다.|
| |`그래서 시프트 연산을 통해 요소가 3개라면 4번재 비트에 1을 추가하여 배열 길이와 동일한 비트 문자열을 만들어 놓고 부분집합을 만들어야 한다.` |
| |`즉, 배열의 요소가 3개라면 1을 3번 좌측 시프트를 한 1000(2) 이진수와 순회시 사용할 숫자와 OR 연산을 한다.` |
| |`만약 0과 1000(2)을 OR 연산하면 1000(2)이 되고 bin()의 결과로 'ob1000'이 반환된다` |
|2 |문자열로 리스트의 슬라이스 연산을 동일하게 적용 가능하니 [3:]을 통해 맨 앞 부터 'ob1'을 잘라내어 '000'의 값을 얻어 낼 수 있다.|
|3 |배열의 요소가 3개라면 0에서 7까지 순회할 것이고, 000, 001,101 순으로 비트 문자열을 만들어 낼 것이다.|
|시간 복잡도|O(n*2^n)|
|공간 복잡도|O(n*2^n) |



### 아이디어1(Bit Manipulation)

```
class Solution:
    def subsets(self, nums: List[int]) -> List[List[int]]:
        res=[]
        nums_len = len(nums)
        nth_bit = 1<<nums_len
        
        for i in range(2**nums_len):
            bitmask = bin(i | nth_bit)[3:]
            
            res.append([nums[j] for j in range(nums_len) if bitmask[j]=='1'])
            
        return res    

```

### 아이디어2

```
class Solution:
    def subsets(self, nums: List[int]) -> List[List[int]]:
        result=[]

        for i in range(len(nums)+1):
            result += list(itertools.combinations(nums,i))

            return result

```



