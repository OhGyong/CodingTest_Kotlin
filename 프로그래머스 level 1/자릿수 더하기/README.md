[자릿수 더하기](https://programmers.co.kr/learn/courses/30/lessons/12931)

나의 풀이
```kotlin
    class Solution {
        fun solution(n: Int): Int {
            var answer=0
            (n.toString()).forEach{answer+=Character.getNumericValue(it)}
            return answer
        }
    } 
```