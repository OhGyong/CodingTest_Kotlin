[수박수박수박수박수박수](https://programmers.co.kr/learn/courses/30/lessons/12922)

나의 풀이
```kotlin
    class Solution {
        fun solution(n: Int): String {
            var answer = ""
            for(i in 1..n){
                if(i%2==0) answer+="박"
                else answer+="수"
            }
            return answer
        }
    }
```