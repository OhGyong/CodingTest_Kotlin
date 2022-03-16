[음양 더하기](https://programmers.co.kr/learn/courses/30/lessons/76501)


나의 풀이
```kotlin
    class Solution {
        fun solution(absolutes: IntArray, signs: BooleanArray): Int {
            var answer: Int = 0
            
            for(i in absolutes.indices){
                when(signs[i]){
                    false-> absolutes[i]=-absolutes[i]
                }
            }
            answer = absolutes.sum()
            return answer
        }
    }
```

foldIndexed를 사용한 풀이
``` kotlin
    class Solution {
        fun solution(absolutes: IntArray, signs: BooleanArray) =
            absolutes.foldIndexed(0) { idx, acc, num -> acc + if (signs[idx]) num else -num }
    }
```