# Missing Number

>Given an array nums containing n distinct numbers in the range [0, n], return the only number in the range that is missing from the array.

-  Example 1:
Input: nums = [3,0,1]
Output: 2
Explanation: n = 3 since there are 3 numbers, so all numbers are in the range [0,3]. 2 is the missing number in the range since it does not appear in nums.

- Example 2: 
Input: nums = [0,1]
Output: 2
Explanation: n = 2 since there are 2 numbers, so all numbers are in the range [0,2]. 2 is the missing number in the range since it does not appear in nums.

- Example 3:
Input: nums = [9,6,4,2,3,5,7,0,1]
Output: 8
Explanation: n = 9 since there are 9 numbers, so all numbers are in the range [0,9]. 8 is the missing number in the range since it does not appear in nums.

## 제한사항
- n 크기의 정수형 배열
- 0 에서 n 사이의 숫자만 갖고 있다.
- 예외적인 경우는 없다고 가정한다.


## 아이디어 

| |아이디어1(Sorting) |아이디어2(Hash Set) |아이디어3(Bit Manipulation) |아이디어 4(Math)|
|----------------|-------------------------------|-----------------------------|-----------------------------|-----------------------------|
|1 |배열을 정렬한다. |배열의 모든 값을 해시 셋(Hash Set)에 넣는다.|변수에 n의 값으로 초기화한다.|0 에서 n까지 합을 구한다.|
|2 |1번째 요소가 0이 아니라면 0을 반환한다.|0에서 n까지 순회한다.|배열을 순회한다.|배열 요소의 총합을 구한다.|
| | |`해시 셋에 없는 값을 반환한다.`|`변수에 현재 인덱스와 해당 값을 다 같이 XOR한다.`||
|3|마지막 요소가 n이 아니라면 n을 반환한다. |변수값을 반환한다.|(0에서 n까지 합)-(배열의 요소의 총합)을 반환한다.|
|4|배열을 1번 인덱스부터 n-1까지 순회한다. ||||
| |`현재 요소가 이전 요소에 1만큼 큰 수가 아니라면 현재 인덱스를 반환한다.`||||
|시간 복잡도|O(nlogn)|O(n)|O(n)|O(n)|
|공간 복잡도|O(1) |O(n)|O(1)|O(1)|



### 아이디어1(Sorting)

```
class Solution:
    def missingNumber(self, nums: List[int]) -> int:
        nums.sort()

        if nums[-1] != len(nums):
            return len(nums)
        if nums[0] != 0:
            return 0

        for i in range(1,len(nums)):
            expected = nums[i-1] +1
            if expected != nums[i]:
                return expected

        return -1               
      

```

### 아이디어2(Hash Set)

```
class Solution:
    def missingNumber(self, nums: List[int]) -> int: 
        set_nums = set(nums)

        for i in range(len(nums)+1):
            if i not in set_nums:
                return i

        return -1                  

```

### 아이디어3(Bit Manipulation)

```
class Solution:
    def missingNumber(self, nums: List[int]) -> int:
        missing = len(nums)

        for i in range(len(nums)):
            missing = missing ^ i ^ nums[i]

        return missing            

```

### 아이디어4(Math)

```
class Solution:
    def missingNumber(self, nums: List[int]) -> int:
        expected_sum=0
        nums_sum=0

        for i in range(len(nums)+1):
            expected_sum += i

        for _, num in enumerate(nums):
            nums_sum +=num

        return expected_sum - nums_sum


<!--가우스 덧셈을 활용  -->
class Solution:
    def missingNumber(self, nums: List[int]) -> int:
        expected_sum = int((len(nums)*(len(nums)+1))/2)
        nums_sum =0

        for _, num in enumerate(nums):
            nums_sum +=num

        return expected_sum-nums_sum

<!-- 가우스 덧셈과 sum()함수 이용 -->
class Solution:
    def missingNumber(self, nums: List[int]) -> int:
        return int((len(nums)*(len(nums)+1))/2) -sum(nums)


```

