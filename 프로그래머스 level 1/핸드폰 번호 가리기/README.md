[핸드폰 번호 가리기](https://programmers.co.kr/learn/courses/30/lessons/12948)

나의 풀이
```kotlin
    class Solution {
        fun solution(phone_number: String): String {
            var s1=phone_number.substring(0 until phone_number.length-4)
            var s2=phone_number.substring(phone_number.length-4 until phone_number.length)
            s1=s1.replace("[0-9]".toRegex(),"*")
            return s1+s2
        }
    }
```