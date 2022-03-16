[부족한 금액 계산하기](https://programmers.co.kr/learn/courses/30/lessons/82612)

나의 풀이
```kotlin
    class Solution {
        fun solution(price: Int, money: Int, count: Int): Long  = (1..count).map { it * price.toLong() }.sum().let { if(money > it) 0 else it - money }
    }
```