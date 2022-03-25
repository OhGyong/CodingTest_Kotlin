[위장](https://programmers.co.kr/learn/courses/30/lessons/42578#)

clothes라는 2차원 배열에서 의상의 종류를 기준으로 개수를 카운트해주고 각 의상 별로 안 입을 수 있기 때문에 각 요소에 1을 더해준 값을 서로 곱하고 반환한다.<br/>
단, 모든 요소에 1을 더했을 경우 아예 입지 않은 경우가 하나 있기 때문에 마지막에 1을 빼주었다.

나의 풀이
```kotlin
    class Solution {
        fun solution(clothes: Array<Array<String>>): Int {
            return clothes.groupingBy{it[1]}.eachCount().values.fold(1){one, ele -> one*(ele+1) } - 1
        }
    }
```