[서울에서 김서방 찾기](https://programmers.co.kr/learn/courses/30/lessons/12919)

나의 풀이
```kotlin
    class Solution {
        fun solution(seoul: Array<String>): String {
            var answer = ""
            seoul.forEachIndexed{index,  it ->
                if(it == "Kim") answer = "김서방은 "+index.toString()+"에 있다"
            }
            return answer
        }
    }
```