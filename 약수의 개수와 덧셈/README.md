[약수의 개수와 덧셈](https://programmers.co.kr/learn/courses/30/lessons/42889)

나의 풀이
```kotlin
    class Solution {
        fun solution(left: Int, right: Int): Int {
            var answer: Int = 0
            for(i in left..right){
                var divisor = 0
                for(j in 1..i){
                    if(i%j==0) divisor++
                }
                if(divisor%2==0){
                    answer+=i
                }else{
                    answer-=i
                }
            }
            return answer
        }
    }
```