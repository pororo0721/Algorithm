# Search Insert Position

>Given a sorted array of distinct integers and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order. You must write an algorithm with O(log n) runtime complexity.


-  Example 1:
Input: nums = [1,3,5,6], target = 5
Output: 2

- Example 2: 
Input: nums = [1,3,5,6], target = 2
Output: 1

- Example 3:
Input: nums = [1,3,5,6], target = 7
Output: 4

## 제한사항
- 정수형 배열
- 정수형 target 변수
- 배열의 값은 정수, 즉 음수, 0, 양수를 포함
- 배열은 정렬되어 있다.
- 배열의 크기는 매우 클 수 있다.

## 아이디어 

|                |아이디어1(Brute-Force)          |아이디어2(Binary Search) |
|----------------|-------------------------------|-----------------------------|
|1 |배열의 각 요소를 인덱스 0에서부터 순회한다. |배열 요소를 이진 탐색으로 접근한다. |       
|2 |순회하면서 target의 값과 같거나 크다면 순회를 중단한다.|요소를 찾는다면, 해당 인덱스를 반환|
|3 |중단된 시점의 인덱스를 반환한다.|끝까지 찾지 못하고 이진 탐색을 종료한다면, 최종 접근했던 낮은 인덱스의 값을 반환한다.|
|시간 복잡도| O(N)|O(logN)|
|공간 복잡도| O(1)|O(1)|


### 아이디어1(Brute-Force)

```
class Solution:
    def searchInsert(self, nums: List[int], target: int) -> int:
        index=0

        while index<= len(nums):
            if target <= nums[index]:
                break

            index+=1

        return index                       

```

### 아이디어2(Binary Search)

```
class Solution:
    def searchInsert(self, nums: List[int], target:int)-> int:
        low=0
        high=len(nums)-1

        while low <=high:
            mid=int((low+high)/2)

            if target == nums[mid]:
                return mid
            if target > nums[mid]:
                low = mid+1
            else:
                hight =mid-1

        return low                
      
```
