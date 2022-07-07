# Two Sum

>You are given two integer arrays nums1 and nums2, sorted in non-decreasing order, and two integers m and n, representing the number of elements in nums1 and nums2 respectively. Merge nums1 and nums2 into a single array sorted in non-decreasing order. The final sorted array should not be returned by the function, but instead be stored inside the array nums1. To accommodate this, nums1 has a length of m + n, where the first m elements denote the elements that should be merged, and the last n elements are set to 0 and should be ignored. nums2 has a length of n.


- Example 1: 
Input: nums1 = [1,2,3,0,0,0], m = 3, nums2 = [2,5,6], n = 3
Output: [1,2,2,3,5,6]
Explanation: The arrays we are merging are [1,2,3] and [2,5,6].
The result of the merge is [1,2,2,3,5,6] with the underlined elements coming from nums1.

- Example 2: 
Input: nums1 = [1], m = 1, nums2 = [], n = 0
Output: [1]
Explanation: The arrays we are merging are [1] and [].
The result of the merge is [1].

- Example 3:
Input: nums1 = [0], m = 0, nums2 = [1], n = 1
Output: [1]
Explanation: The arrays we are merging are [] and [1].
The result of the merge is [1].
Note that because m = 0, there are no elements in nums1. The 0 is only there to ensure the merge result can fit in nums1.

## 제한사항
- 주어진 nums1, nums2의 요소들은 정렬되어 있다.
- nums1에 요소들은 m개 있다.
- nums2에 요소들은 n개 있다.
- nums1 배열의 크기는 n+m이다.

## 아이디어 

|                |아이디어1(Sorting)          |아이디어2(Two Pointers) |
|----------------|-------------------------------|-----------------------------|
|1 |nums2의 요소를 nums1의 확보된 추가 공간에 삽입한다.| nums1을 위한 인덱스 포인터 i, nums1의 마지막 요소를 가리킴(m-1) |       
|2 |sorted()함수를 이용해 정렬 |nums2를 위한 인덱스 포인터 j, nums2의 마지막 요소를 가리킴 (n-1) |
|3 | |삽입을 위한 포인터 k, nums1 공간 마지막을 가리킴 (m+n-1) |
|4 | |현재 i와 j의 값을 비교한다. |
|5 | |비교하여 큰 쪽의 값을 k의 위치에 추가한다. |
|  | |`k는 감소한다.` |
|  | |`비교하여 큰 쪽 인덱스 값이 k에 추가되었으므로 큰 쪽의 인덱스는 1 감소한다.` |
|6 | |i,j 중 하나라도 0보다 작아지면 비교를 중지한다. |
|7 | |j가 아직 0보다 크다면 nums1을 가리키고 있는 k 값을 감소시키면서 nums1에 삽입한다. |
|시간 복잡도| O(NlogN)|O(N+M)|
|공간 복잡도| O(N)|O(1)|



### 아이디어1(Brute-Force)

```
class Solution:
    def merge(self, nums1: List[int], m: int, nums2: List[int], n: int) -> None:
        for i, v in enumerate(nums2):
            nums1[m+i] = v

        nums1[:] = sorted(nums1)              

```

### 아이디어2(Hash Table)

```
class Solution:
    def merge(self, nums1: List[int], m: int, nums2: List[int], n: int) -> None:
        i= m-1
        j= n-1
        k= m+n-1

        while i>=0 and j>=0:
            if nums1[i] < nums2[j]:
                nums1[k] = nums2[j]
                j-=1
            else:
                nums1[k]= nums1[i]
                i-=1
        k-=1

        while j>=0:
            nums1[k]=nums2[j]
            k -=1
            j -=1

```
