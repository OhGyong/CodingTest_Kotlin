[최대공약수와 최소공배수](https://programmers.co.kr/learn/courses/30/lessons/12940)

유클리드 호제법을 사용.

나의 풀이
```kotlin
    class Solution {
        fun solution(n: Int, m: Int): IntArray {
            return intArrayOf(gcm(n, m), lcm(n, m))
        }

        fun gcm(a: Int, b: Int): Int {
            var maximum = Math.max(a, b)
            var minimum = Math.min(a, b)
            if (minimum == 0) {
                return maximum
            } else {
                return gcm(minimum, maximum % minimum)
            }
        }

        fun lcm(a: Int, b: Int): Int = (a * b) / gcm(a, b)
    }
```