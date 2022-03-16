[정수 내림차순으로 배치하기](https://programmers.co.kr/learn/courses/30/lessons/12933)

나의 풀이
```kotlin
    class Solution {
        fun solution(n: Long): Long = n.toString().map{it}.sortedDescending().joinToString("").toLong()
    }
```