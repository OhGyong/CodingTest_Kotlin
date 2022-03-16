[나머지가 1이 되는 수 찾기](https://programmers.co.kr/learn/courses/30/lessons/87389)

나의 풀이
```kotlin
    class Solution {
        fun solution(n: Int): Int {
            var answer: Int = 0
            
            for(i in 2..n){
                if(n%i == 1){
                    answer = i
                    break
                }
            }
            return answer
        }
    }
```