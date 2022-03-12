[최소직사각형](https://programmers.co.kr/learn/courses/30/lessons/86491)

sizes라는 이차원 배열에서 가로길이와 세로길이 중에서 더 긴 방향이 세로배열에 위치되도록 설정을 해주고</br>
재배치된 배열에서 가로배열에서 가장 큰 값과 세로배열에서 가장 큰 값을 구해서 반환해주었다.

나의 풀이
```kotlin
    class Solution {
        fun solution(sizes: Array<IntArray>): Int {
            
            var wMax = 0
            var hMax = 0

            for(i in sizes){
                var temp = 0
                if(i[0]>i[1]){
                    temp = i[0]
                    i[0] = i[1]
                    i[1] = temp
                }

                if(i[0]>wMax) wMax=i[0]
                if(i[1]>hMax) hMax=i[1]
            }
            return wMax*hMax
        }
    }
```