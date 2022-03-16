[짝수와 홀수](https://programmers.co.kr/learn/courses/30/lessons/12937)

나의 풀이
```kotlin
    class Solution {
        fun solution(num: Int): String = num.let{if(num%2==0) "Even" else "Odd"}
    }
```