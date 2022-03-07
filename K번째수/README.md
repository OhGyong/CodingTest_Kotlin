[K번째수](https://programmers.co.kr/learn/courses/30/lessons/42748)

나는 sliceArray로 배열을 반환해주었는데, 다른 사람의 풀이를 보면 slice를 사용하는 대신 map을 사용해서 배열로 반환을 해준 차이가 있었다.

나의 풀이
```kotlin
    class Solution {
        fun solution(array: IntArray, commands: Array<IntArray>): IntArray {
            var answer = IntArray(commands.size)
            
            var idx = 0
            commands.forEach{
                var newArray = array.sliceArray((it[0]-1)..(it[1]-1)).sorted()
                answer[idx] = newArray[it[2]-1]
                idx++
            }
            return answer
        }
    }
```

다른 사람 풀이
```kotlin
    class Solution {
        fun solution(array: IntArray, commands: Array<IntArray>): IntArray {
            return commands.map { command ->
                array.slice(IntRange(command[0] - 1, command[1] - 1)).sorted()[command[2] - 1]
            }.toIntArray()    
        }
    }
```