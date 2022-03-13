[문자열 내 마음대로 정렬하기](https://programmers.co.kr/learn/courses/30/lessons/12915)

sortBy로 배열 내 문자열을 정렬하였다.

나의 풀이
```kotlin
    class Solution {
        fun solution(strings: Array<String>, n: Int): Array<String> {
            return strings.also {
                it.sort()
                it.sortBy { it[n] }
            }
        }
    }
```