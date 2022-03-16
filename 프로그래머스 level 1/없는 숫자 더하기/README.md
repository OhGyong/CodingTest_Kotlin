[신고 결과 받기](https://programmers.co.kr/learn/courses/30/lessons/92334)

```kotlin
    class Solution {
        fun solution(numbers: IntArray): Int {
            var answer: Int = 0
            var numArray = Array(10, {i -> i})
            numArray.forEach{ if(!numbers.contains(it)) answer +=it }
            return answer
        }
    }
```
