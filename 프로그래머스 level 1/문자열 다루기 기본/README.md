[문자열 다루기 기본](https://programmers.co.kr/learn/courses/30/lessons/12918)

문자열의 길이를 먼저 비교해서 4 또는 6일때 정규식을 사용한다.<br/>
숫자 이외의 값을 제거한 문자열과 제공된 문자열을 비교하여 다르면 다른 문자가 있던 것으로 판단하고 false로 설정해준다.

<br/><br/>

다른 사람 풀이에서 길이 비교 이후에 자연수로된 문자열이라면 정수로 변경이 가능하므로 toIntOrNull()을 이용해서 쉽게 구한것을 알 수 있다.

나의 풀이
```kotlin
    class Solution {
        fun solution(s: String): Boolean {
            var answer=true
            if(s.length == 4 || s.length ==6){
                var number = s.replace("[^0-9]".toRegex(),"")
                if(s != number) answer=false 
            }else answer=false
            return answer
        }
    }
```

다른 사람 풀이
```kotlin
    class Solution {
        fun solution(s: String) = (s.length == 4 || s.length == 6) && s.toIntOrNull() != null
    }
```