[숫자 문자열과 영단어](https://programmers.co.kr/learn/courses/30/lessons/81301)

```kotlin
    class Solution {
        fun solution(s: String): Int {
            var answer: Int = 0
            answer = s.replace("zero".toRegex(),"0")
                    .replace("one".toRegex(),"1")
                    .replace("two".toRegex(),"2")
                    .replace("three".toRegex(),"3")
                    .replace("four".toRegex(),"4")
                    .replace("five".toRegex(),"5")
                    .replace("six".toRegex(),"6")
                    .replace("seven".toRegex(),"7")
                    .replace("eight".toRegex(),"8")
                    .replace("nine".toRegex(),"9")
                    .toInt()
            return answer
        }
    }
}
```