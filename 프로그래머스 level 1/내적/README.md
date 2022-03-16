[내적](https://programmers.co.kr/learn/courses/30/lessons/70128)

나의 풀이
```kotlin
    class Solution {
        fun solution(a: IntArray, b: IntArray): Int {
            var answer: Int = 0
            answer = a.foldIndexed(0){
                idx, result, element ->
                result + element*b[idx]
            }
            return answer
        }
    }
```