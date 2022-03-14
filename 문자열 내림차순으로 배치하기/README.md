[문자열 내림차순으로 배치하기](https://programmers.co.kr/learn/courses/30/lessons/12917)

sortBy로 배열 내 문자열을 정렬하였다.

나의 풀이
```kotlin
    class Solution {
        fun solution(s: String): String {
            return String(s.toCharArray().sortedArrayDescending())
        }
    }
```