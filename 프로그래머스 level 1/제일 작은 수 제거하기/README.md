[제일 작은 수 제거하기](https://programmers.co.kr/learn/courses/30/lessons/12935)

나는 리스트로 변경해서 최소값의 인덱스를 찾아서 해결했는데, </br>
다른 사람 풀이에서처럼 filter() 함수를 써서 최소값을 제외한 배열을 반환하면 더 쉽게 할 수 있었다.

나의 풀이
```kotlin
    class Solution {
        fun solution(arr: IntArray): IntArray {
            var answer = intArrayOf()
            if(arr.size == 1) return intArrayOf(-1)
            var list = arr.toMutableList()
            list.removeAt(list.indexOf(list.minOrNull()))
            return list.toIntArray()
        }
    } 
```

다른 사람 풀이
```kotlin
    class Solution {
        fun solution(arr: IntArray): IntArray = if(arr.size == 1) arrayOf(-1).toIntArray() 
                                                else arr.filter { it != arr.min() }.toIntArray()
    }
```