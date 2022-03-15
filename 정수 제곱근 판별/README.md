[정수 제곱근 판별](https://programmers.co.kr/learn/courses/30/lessons/12934)

나의 풀이
```kotlin
    import kotlin.math.pow

    class Solution {
        fun solution(n: Long): Long {
            var answer: Long = -1
            
            var sqrt:Long = -1
            for(i in 1..n){
                if(i*i==n){
                    sqrt = i.toLong()
                    break
                }
            }
            if(sqrt != -1.toLong()) answer= ((sqrt+1)*(sqrt+1)).toLong()
            
            return answer
        }
    }
```