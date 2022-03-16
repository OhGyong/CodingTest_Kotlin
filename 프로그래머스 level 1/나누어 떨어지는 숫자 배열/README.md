[나누어 떨어지는 숫자 배열](https://programmers.co.kr/learn/courses/30/lessons/12910)

나의 풀이
```kotlin
    class Solution {
        fun solution(arr: IntArray, divisor: Int): IntArray {
            var answer = mutableListOf<Int>()
            var total = 0
            arr.forEach{
                if(it%divisor == 0){
                    answer.add(it)                
                    total++
                }
            }
            if(total == 0) answer.add(-1)
            return answer.sorted().toIntArray()
        }
    }
```