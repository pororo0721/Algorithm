# Group Anagrams

>Given an array of strings strs, group the anagrams together. You can return the answer in any order. An Anagram is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.


- Example 1: 
Input: strs = ["eat","tea","tan","ate","nat","bat"]
Output: [["bat"],["nat","tan"],["ate","eat","tea"]]

- Example 2: 
Input: strs = [""]
Output: [[""]]

- Example 3:
Input: strs = ["a"]
Output: [["a"]]

## 제한사항
- 문자열 리스트
- 리스트에 있는 모든 문자열은 소문자로 구성


## 아이디어 

|                |아이디어1(Hash Table, Sorting)          |아이디어2(Hash Table, 문자 카운트 ) |
|----------------|-------------------------------|-----------------------------|
|1 |해시 테이블 생성| 해시 테이블 생성 |       
|  |`키로 문자열, 값으로 리스트를 가진다.` |`키로 a~z까지 문자 개수 튜플, 값으로 리스트를 가진다.`|
|2 |입력 문자열 리스트를 순회 |입력 문자열 리스트를 순회 |
|  |`문자열을 정렬` |`각 문자열의 문자를 순회하며 카운트 한다.` |
|  |`정렬된 문자열을 키로 찾은 리스트에 문자열을 추가` |`만들어진 문자 카운트 배열을 기준으로 해시 테이블에서 키로 찾고, 같은 키를 가지는 문자열을 값으로 추가한다.`|
|시간 복잡도| O(N*NlogL) n은 문자열 총개수, L은 문자열 중 가장 긴 문자열 길이 |O(N * L)|
|공간 복잡도| O(N*L)|O(N * L)|



### 아이디어1(Hash Table, Sorting)  

```
class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        hashmap=collections.defaultdict(list)

        for s in strs:
            hashmap["".join(sorted(s))].append(s)
            
        return hashmap.values()               

```

### 아이디어2(Hash Table, 문자 카운트 )

```
class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        hashmap=collections.defaultdict(list)
        
        for s in strs:
            count =[0]*26
            
            for ch in s:
                count[ord(ch)-ord('a')] +=1
            hashmap[tuple(count)].append(s)    
            
        return hashmap.values()    

```
