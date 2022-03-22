[멀쩡한 사각형](https://programmers.co.kr/learn/courses/30/lessons/62048)

유클리드 호제법을 이용해서 최대공약수를 구해서 해결하였다.<br/>
규칙을 찾지 못해 검색해서 구했는데 `가로+세로-최대공약수` 찾아내는 것이 중요했다.

나의 풀이
```kotlin
    class Solution {
        fun solution(w: Int, h: Int): Long {
            var answer: Long = w.toLong()*h.toLong() - (w.toLong() + h.toLong() - gcd(w,h).toLong())
            return answer
        }
        
        fun gcd(w: Int, h: Int): Int{
            if(h == 0) return w
            else return gcd(h, w%h)
        }
    }
```