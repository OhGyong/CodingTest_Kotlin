[두 정수 사이의 합](https://programmers.co.kr/learn/courses/30/lessons/12912)

나의 풀이
```kotlin
    class Solution {
        fun solution(a: Int, b: Int): Long {
            var answer: Long = 0
            var a= a
            var b= b
            if(a==b) answer = a.toLong()
            else{
                var temp = a
                if(a>b){
                    a=b
                    b=temp
                }
                for(i in a..b){
                    answer+=i.toLong()
                }
            }
            return answer
        }
    }
```