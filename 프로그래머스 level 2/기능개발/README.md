[기능개발](https://programmers.co.kr/learn/courses/30/lessons/42586)

첫 실패하는 부분에서 for과 while 루프를 이용해서 카운트를 생각했는데 어느 부분이 틀렸는지 파악도 힘들고 가독성이 별로 였다.<br/>
비교 값을 하나 정해두고 forEach문으로 it과 비교 값을 비교하는 것이 훨씬 가독성이 좋았다.

나의 풀이 실패
```kotlin
    /*
    1. dayList라는 리스트를 만들어서 progresses의 원소들이 speeds로 인해 100%가 되는데 걸리는 날짜를 계산해서 담는다.
    2. dayList를 돌면서 자신보다 날짜가 높기 전까지 돌면서 1씩 카운트한다.
    3. 1씩 카운트한 값을 결과를 리스트에 담아서 총합이 size를 벗어나면 루프문을 탈출하고 반환
    */
    class Solution {
        fun solution(progresses: IntArray, speeds: IntArray): IntArray {
            var dayList = mutableListOf<Int>()
            for(i in progresses.indices){
                var cnt = 0
                var point = progresses[i]
                while(point<100){
                    point+=speeds[i]
                    cnt++
                }
                dayList.add(cnt)
            }
            
            var resultList = mutableListOf<Int>()
            for(j in dayList.indices){
                var cnt = 1
                var k = j+1
                while(k<dayList.size-1){
                    if(dayList[j]<dayList[k]) break
                    cnt++
                    k++
                }
                if(resultList.sum()>=progresses.size) break
                resultList.add(cnt)
            }
            return resultList.toIntArray()
        }
    }
```

나의 풀이 성공
```kotlin
    class Solution {
        fun solution(progresses: IntArray, speeds: IntArray): IntArray {
            var dayList = mutableListOf<Int>()
            for(i in progresses.indices){
                var cnt = 0
                var point = progresses[i]
                while(point<100){
                    point+=speeds[i]
                    cnt++
                }
                dayList.add(cnt)
            }
            
            var resultList = mutableListOf<Int>()
            var first = dayList[0]
            var count = 0

            dayList.forEach{
                if(first<it){
                    first = it
                    resultList.add(count)
                    count = 0
                }
                count++
            }
            resultList.add(count)
            return resultList.toIntArray()
        }
    }
```