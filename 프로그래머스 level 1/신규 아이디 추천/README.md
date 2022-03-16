[신규 아이디 추천](https://programmers.co.kr/learn/courses/30/lessons/72410)

```kotlin
    class Solution {
        fun solution(new_id: String): String {
            // 1단계
            var answer: String = new_id.toLowerCase()

            // 2단계
            answer = answer.replace("[^a-z0-9_.-]".toRegex(), "")

            // 3단계
            answer = answer.replace("[.]{2,}".toRegex(), ".")

            // 4단계
            answer = answer.replace("^[.]|[.]$".toRegex(), "")

            // 5단계
            answer = answer.replace("^$".toRegex(), "a")

            // 6단계
            if(answer.length > 15){
                answer = answer.slice(0..14)
                answer = answer.replace("[.]$".toRegex(), "")
            }

            // 7단계
            if(answer.length <= 2){
                val plusWord = answer.substring(answer.length-1)
                while(answer.length<3){
                    answer = answer + plusWord
                }
            }
            
            return answer
        }
    }
```
