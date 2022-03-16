[약수의 합](https://programmers.co.kr/learn/courses/30/lessons/12928)

나의 풀이
```kotlin
    class Solution {
        fun solution(n: Int): Int {
            var answer=0
            for(i in 1..n){
                if(n%i==0) answer+=i
            }
            return answer
        }
    }
```