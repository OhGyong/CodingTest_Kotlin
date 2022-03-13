[자연수 뒤집어 배열로 만들기](https://programmers.co.kr/learn/courses/30/lessons/12932#)

나의 풀이
```kotlin
    class Solution {
        fun solution(n: Long): IntArray {
            var answer = mutableListOf<Int>()
            var newString = n.toString().reversed()
            newString.forEach{answer.add(Character.getNumericValue(it))}
            return answer.toIntArray()
        }
    }
```