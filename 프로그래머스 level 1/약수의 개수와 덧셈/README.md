[약수의 개수와 덧셈](https://programmers.co.kr/learn/courses/30/lessons/77884)

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
                if(divisor%2==0) answer+=i
                else answer-=i
            }
            return answer
        }
    }
```

다른 사람 풀이
```kotlin
    class Solution {
        fun solution(left: Int, right: Int): Int {
            return (left..right).map { i -> if ((1..i).filter { i % it == 0 }.size % 2 == 0) i else -i }.sum()
        }
    }
```