[이상한 문자 만들기](https://programmers.co.kr/learn/courses/30/lessons/12930)

내가 푼 풀이로 4,5,8,9,11에서 실패를 했다.

나의 풀이
```kotlin
    class Solution {
        fun solution(s: String): String {
            var answer=""
            val array=s.split(" ")
            array.forEach{
                it.forEachIndexed{ index, it->
                    if(index%2==0) answer+=it.toUpperCase()
                    else answer+=it.toLowerCase()
                }
                if(it != array[array.size-1]) answer += " "
            }
            return answer
        }
    }
```

다른 사람 풀이
```kotlin
    class Solution {
        fun solution(s: String): String =
            s.split(" ").joinToString(" ") {
                it.mapIndexed { i, c ->
                    when (i % 2) {
                        0 -> c.toUpperCase()
                        else -> c.toLowerCase()
                    }
                }.joinToString("")
            }
    }
```