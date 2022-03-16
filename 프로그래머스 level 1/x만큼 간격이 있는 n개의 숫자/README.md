[x만큼 간격이 있는 n개의 숫자](https://programmers.co.kr/learn/courses/30/lessons/12954)

나의 풀이
```kotlin
    class Solution {
        fun solution(x: Int, n: Int): LongArray {
            var answer=LongArray(n)
            for(i in 0 until n){
                answer[i]=x.toLong() * (i+1)
            }
            return answer
        }
    }
```

다른 사람 풀이
```kotlin
    class Solution {
        fun solution(x: Int, n: Int): LongArray = LongArray(n) { x.toLong() * (it + 1) }
    }
```