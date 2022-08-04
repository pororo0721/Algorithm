# Valid Palindrome

>A phrase is a palindrome if, after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters, it reads the same forward and backward. Alphanumeric characters include letters and numbers. Given a string s, return true if it is a palindrome, or false otherwise.


-  Example 1:
Input: s = "A man, a plan, a canal: Panama"
Output: true
Explanation: "amanaplanacanalpanama" is a palindrome.

- Example 2: 
Input: s = "race a car"
Output: false
Explanation: "raceacar" is not a palindrome.

- Example 3:
Input: s = " "
Output: true
Explanation: s is an empty string "" after removing non-alphanumeric characters.
Since an empty string reads the same forward and backward, it is a palindrome.

## 제한사항
- 문자열의 입력, true 혹은 false 반환
- 비어 있는 문자열은 회문


## 아이디어 

|                |아이디어1(Two Pointer)          |아이디어2(String) |
|----------------|-------------------------------|-----------------------------|
|1 |i는 0에서 시작하고, j는 문자열의 끝에서 시작 | 해시 테이블을 구성한다. |알파벳과 숫자만 남기고 제거  |      
|2 |i가 j보다 작을 때까지 |`키 값으로는 배열의 요소, 값으로는 요소의 인덱스로 구성` |소문자로 변환|
|  |`i 위치에 문자가 알파벳 혹은 숫자가 아니라면, i+1` | |
|  |`j 위치에 문자가 알파벳 혹은 숫자가 아니라면, j-1` ||
|  |`i 위치와 j 위치의 문자가 같은지 비교` |`목표값 - 현재요소 = 다른요소`|
|  |`같지 않다면, false 반환`            |`해시테이블에서 다른 요소의 값을 찾는다.`|
|3 |모두 확인이 되었다면, true 반환      |변환 완료된 문자열과 해당 문자열을 뒤집은 문자열을 비교하여 같으면 true 반환, 다르면 false 반환|
|시간 복잡도| O(N)|O(N)|
|공간 복잡도| O(1)|O(N)|



### 아이디어1(Two Pointer)

```
class Soultion:
    def isPalindrome(s:str)->bool:
        i=0
        j=len(s)-1

        s=s.lower()

        while i<j:
            while i<j:
                if s[i].isalnum():
                    break
                i+=1

            while i<j:
                if s[j].isalnum():
                    break
                j-=1

            if s[i] !=s[j]:
                return False

            i+=1
            j-=1

        return True                            

```

### 아이디어2(String)

```
class Solution:
    def isPalindrome(s: str) ->bool:
        s="".join(list(filter(str.isalnum,s))).lower()

        return s = s[::-1]
     

```
