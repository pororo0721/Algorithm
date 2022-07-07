# Remove Duplicates from Sorted Array

>Given an integer array nums sorted in non-decreasing order, remove the duplicates in-place such that each unique element appears only once. The relative order of the elements should be kept the same. Since it is impossible to change the length of the array in some languages, you must instead have the result be placed in the first part of the array nums. More formally, if there are k elements after removing the duplicates, then the first k elements of nums should hold the final result. It does not matter what you leave beyond the first k elements. Return k after placing the final result in the first k slots of nums. Do not allocate extra space for another array. You must do this by modifying the input array in-place with O(1) extra memory.


-  Example 1:
Input: nums = [1,1,2]
Output: 2, nums = [1,2,_]
Explanation: Your function should return k = 2, with the first two elements of nums being 1 and 2 respectively.
It does not matter what you leave beyond the returned k (hence they are underscores).

- Example 2: 
Input: nums = [0,0,1,1,1,2,2,3,3,4]
Output: 5, nums = [0,1,2,3,4,_,_,_,_,_]
Explanation: Your function should return k = 5, with the first five elements of nums being 0, 1, 2, 3, and 4 respectively.
It does not matter what you leave beyond the returned k (hence they are underscores).


## 제한사항
- 정수형 배열 (입력)
- 입력으로 주어지는 배열의 길이는 0일 수도 있다.
- 추가 배열 할당 없이 입력 배열을 그대로 수정해야 한다.
- 반환 값은 정수이며, 배열의 길이보다 작거나 같다.


## 아이디어 

|                |아이디어1(Brute-Force)        |
|----------------|-----------------------------|
|1               |맨 첫 요소(curr)를 저장한다.  |
|2               |배열의 요소를 맨 첫 요소를 제외하고 순회한다. |
|                |`1에서 n-1까지 순회` |
|                |`curr과 값이 같다면 다음 요소로 넘어간다.` |
|                |`curr과 값이 같지 않다면, curr을 현재 값으로 업데이트하고 count값을 하나 증가 시킨다.` |
|                |`count 값을 증가시키기 전에 count가 인덱스가 되어 해당 공간에 달라진 curr 값으로 업데이트한다.` |
|시간 복잡도      | O(N) 배열의 모든 요소 n개를 순회해야 한다.|
|공간 복잡도      | O(1)                                   |



### 아이디어1(Brute-Force)

```
class Solution:
    def removeDuplicates(self, nums: List[int]) -> int:
        if len(nums)<=0:
            return 0

        curr=nums[0]
        cnt=1

        for i in range(1,len(nums)):
            if curr !=nums[i]:
                curr=nums[i]
                nums[cnt]=curr
                cnt+=1

        return cnt        

                   

```