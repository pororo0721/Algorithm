# Two Sum

>Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target. You may assume that each input would have exactly one solution, and you may not use the same element twice. You can return the answer in any order.

## 제한사항
- 정수형 배열
- 두수의 합이 정수형을 초과할 수 있는가? -문제에 언급이 없음
- 두수의 합 값이 배열 내에 무조건 존재하는가? -무조건 하나의 해결책이 존재
- 중복된 요소의 값을 2번 이상 사용하여 결과값을 만들어서는 안됨

## 아이디어 

|                |아이디어1(Brute-Force)          |아이디어2(Hash Table) |
|----------------|-------------------------------|-----------------------------|
|1 |배열의 모든 요소의 조합을 찾는다. | 해시 테이블을 구성한다. |       
|  |`루프는 i= 0~n, j=i+1~n으로 2중 루프를 구성` |`키 값으로는 배열의 요소, 값으로는 요소의 인덱스로 구성` |
|  |`1번 루프는 (n번), 2번째 루프는 (n-1)을 기준으로 n*(n-1)로 계산`  | |
|2 | 해당 조합으로 목표값(target)과 비교하여 같다면| 각 요소를 순회하면서 |
|  |`해당 루프를 종료하고 각 값을 가진 인덱스를 반환한다` |`목표값 - 현재요소 = 다른요소`|
|  |                                               |`해시테이블에서 다른 요소의 값을 찾는다.`|
|  |                                               |`만약 다른 요소가 해시 테이블에 있다면, 현재 요소의 인덱스와 해시 테이블의 값 (인덱스)을 반환한다.`|
|  |                                               |`다른 요소가 없다면, 현재 요소를 해시 테이블의 키 값으로 넣고 인덱스를 해시 테이블의 값 항목으로 추가`|
|시간 복잡도| O(n2)|O(n)|
|공간 복잡도| O(1)|O(n)|

> Tip: 배열에서 중복값을 찾거나 순회하면서 특정 값을 쉽게 찾을 수 있는 방법으로 해시 테이블을 많이 사용. 문제에 "중복"이라는 말이 나온다면 해시 테이블을 검토하길 바람

### 아이디어1(Brute-Force)

```
class Soultion:
    def twoSum(self, nums: list[int], target: int)->list[int]:
        for i in range(len(nums)):
            for j in range(i+1,len(nums)):
                if nums[i]+nums[j] == target:
                    return [i,j]
    return [-1,-1]                

```

### 아이디어2(Hash Table)

```
class Solution:
    def twoSum(self, nums:list[int], targete:int)-> list[int]:
        hashtable_dict={}

        for in range(len(nums)):
            value=target-nums[i]

            if hashtable_dict.get(value) is not None and hastable_dict[value] !=i:
                return sorted([i,hashtable_dict[value]])

            hashtable_dict(nums[i])=i
            
        return [-1,1]        

```