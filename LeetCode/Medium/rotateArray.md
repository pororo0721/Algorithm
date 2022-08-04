# Rotate Array

>Given an array, rotate the array to the right by k steps, where k is non-negative.


-  Example 1:
Input: nums = [1,2,3,4,5,6,7], k = 3
Output: [5,6,7,1,2,3,4]
Explanation:
rotate 1 steps to the right: [7,1,2,3,4,5,6]
rotate 2 steps to the right: [6,7,1,2,3,4,5]
rotate 3 steps to the right: [5,6,7,1,2,3,4]

- Example 2: 
Input: nums = [-1,-100,3,99], k = 2
Output: [3,99,-1,-100]
Explanation: 
rotate 1 steps to the right: [99,-1,-100,3]
rotate 2 steps to the right: [3,99,-1,-100]

## 제한사항
- 정수형 배열
- k 값은 양의 정수


## 아이디어 

| |아이디어1(Brute-Force) |아이디어2(Temporary Variable) |아이디어3 |아이디어 4(Math)|
|----------------|-------------------------------|-----------------------------|-----------------------------|-----------------------------|
|1 |k번 만큼 순회한다. |입력과 같은 크기의 임시 배열(temp)을 생성한다.|모든 요소가 한 번씩 교환이 될 때까지 배열을 순회한다.|전체 숫자를 뒤집는다.|
|2 |배열의 요소를 1칸씩 우측으로 이동 및 회전시킨다.|nums 배열을 순회한다.|요소를 k만큼 이동 및 저장한다.|처음 k만큼까지 숫자를 뒤집는다.|
| | |`temp 배열에 nums의 요소를 k 만큼 이동 및 회전 시킨 위치에 값을 삽입한다.`|`이동한 위치의 이전 요소는 저장한다.`||
| | ||`저장한 요소는 다음 k 만큼 이동하여 넣는다.`||
| | ||`시작한 요소까지 값을 이동시키면 해당 순회를 종료한다.`||
| | ||`이동시킬 때마다 카운트한다.`||
| | ||`다음 요소를 선택하고 다시 2번의 내용을 반복한다.`||
|3 | |임시 배열을 순회한다.||이전에 뒤집은 숫자 다음(n-k) 부터 마지막(n)까지 뒤집는다.|
| | |`temp 배열의 요소를 nums 배열에 같은 인덱스의 값을 복사한다.`||
|시간 복잡도|O(n*k)|O(n)|O(n)|O(n)|
|공간 복잡도|O(1) |O(n)|O(1)|O(1)|



### 아이디어1(Brute-Force)

```
class Solution:
    def rotate(self, nums: List[int], k: int) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """ 
        for _ in range(k):
            prev= nums[len(nums)-1]
            for i in range(len(nums)):
                temp = nums[i]
                nums[i]=prev
                prev=temp            

```

### 아이디어2(Temporary Variable)

```
class Solution:
    def rotate(self, nums: List[int], k: int) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """ 
        temp=[0]*len(nums)

        for i, elem in enumerate(nums):
            temp[(i+k)% len(nums)] = nums[i]

        nums[:] =temp    
                 

```

### 아이디어3

```
class Solution:
    def rotate(self, nums: List[int], k: int) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """ 
        count =0

        for start in range(len(nums)):
            if count >= len(nums):
                break

            curr_index= start
            prev_elem = nums[start]

            while True:
                next_index = (curr_index +k) % len(nums)
                temp = nums[next_index]
                nums[next_index] = prev_elem
                prev_elem = temp

                curr_index = next_index
                count+=1

                if curr_index == start:
                    break    
              

```

### 아이디어4(Math)

```
class Solution:
    def rotate(self, nums: List[int], k: int) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """ 
        k= k%len(nums)

        nums[:]= nums[::-1]
        nums[0:k]= nums[0:k][::-1]
        nums[k:len(nums)]=nums[k:len(nums)][::-1]
              

```

