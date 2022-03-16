[가운데 글자 가져오기](https://programmers.co.kr/learn/courses/30/lessons/12903)

나의 풀이
```kotlin
    class Solution {
        fun solution(s: String): String = s.let{if(it.length%2==0) it[it.length/2-1].toString()+it[it.length/2].toString() else it[it.length/2].toString() } 
    }
```