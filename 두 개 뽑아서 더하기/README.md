[두 개 뽑아서 더하기](https://programmers.co.kr/learn/courses/30/lessons/68644)

나의 풀이
```kotlin
    class Solution {
        fun solution(numbers: IntArray): IntArray {
            var answer = mutableListOf<Int>()
            
            for(i in 0 until numbers.size-1){
                for(j in i+1 until numbers.size){
                    answer.add(numbers[i]+numbers[j])
                }
            }
            return answer.distinct().sorted().toIntArray()
        }
    }
```