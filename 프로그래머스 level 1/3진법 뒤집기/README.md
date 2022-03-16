[3진법 뒤집기](https://programmers.co.kr/learn/courses/30/lessons/68935)

나의 풀이
```kotlin
    class Solution {
        fun solution(n: Int): Int {
            var answer: Int = n.toString(3).reversed().toInt(3)
            return answer
        }
    }
```