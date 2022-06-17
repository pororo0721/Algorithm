# Majority Element

>Given an array nums of size n, return the majority element. The majority element is the element that appears more than ⌊n / 2⌋ times. You may assume that the majority element always exists in the array.


-  Example 1:
Input: nums = [3,2,3]
Output: 3

- Example 2: 
Input: nums = [2,2,1,1,1,2,2]
Output: 2


## 제한사항
- 정수형 배열
- 배열은 1개 이상의 요소를 가진다.
- 다수의 수는 무조건 하나가 존재한다.


## 아이디어 

| |아이디어1(Brute-Force) |아이디어2(Hash Table) |아이디어3(Sorting) |
|----------------|-------------------------------|-----------------------------|-----------------------------|
|1 |배열을 순회한다|해시 테이블에서 키 항목으로는 배열의 요소로 하고 값 항목으로는 횟수를 지정한다. |배열을 정렬한다.|
|2 |각 배열의 요소를 다른 모든 요소와 비교하여 배열에 들어있는지 파악한다. |배열을 순회한다.|가운데 수를 반환한다.|
|3 |개수를 세면서 다수의 수 조건에 맞는 숫자가 있으면 숫자를 반환한다. |배열을 순회하면서 해당 요소를 해시 테이블에서 찾는다. |
| | |`값이 있다면 해당 요소를 키 값으로 하는 값 항목을 꺼내 1을 더해 업데이트 한다.`|
| | |`값이 없다면, 해당 요소를 키 항목으로 두고 1의 값으로 추가한다.`|
|4| |값을 업데이트 하고 다수의 수 조건에 맞는 숫자를 반환한다.|
|시간 복잡도| O(n2)|O(n)|O(nlogn)|
|공간 복잡도| O(1) |O(n), 최악의 경우 요소 만큼 해시 테이블이 만들어져야 한다.|O(1)|



### 아이디어1(Brute-Force)

```
class Solution:
    def majorityElement(self, nums: List[int]) -> int:
        majority_count= int(len(nums)/2)

        for i, item_i in enumerate(nums):
            count=0
            for j, item_j in enumerate([i:],start=i):
                if item_i== item_j:
                    count +=1
                if count > majority_count:
                    return item_i

        return -1                         

```

### 아이디어2(Hash Table)

```
class Solution:
    def majorityElement(self, nums: List[int]) -> int:
        majority_count=int(len(num)/2)
        hashmap={}

        for num in nums:
            if hashmap.get(num) != None:
                hashmap[num] = hashmap[num] +1
            else:
                hashmap[num]=1
            if hashmap[num] > majority_count
                return num

        return -1                    

```

### 아이디어3(Sorthing)

```
class Solution:
    def majorityElement(self, nums: List[int]) -> int:
        return sorted(nums)[int(len(nums))/2]                   

```

