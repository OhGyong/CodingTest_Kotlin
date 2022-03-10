[실패율](https://programmers.co.kr/learn/courses/30/lessons/42889)

스테이지에 도달한 플레이어 수와 실패율 계산까지는 무난하게 했지만, 스테이지의 번호를 반환하는 부분에서 오래 걸렸다.</br>
처음에 실패율을 sortedDescending을 통해서 내림차순을 구했는데, 여기서 인덱스로 내림차순을 구하는 방법은 없을까 고민하다가</br>
버블 정렬로 실패율을 내림차순 할때 스테이지를 저장한 배열도 함께 내림차순 정렬해주는 것으로 해결했다.</br>
확실히 실행 시간이 오래걸려서 다른 풀이 방법을 사용해야 하는 것 같다.

나의 풀이
```kotlin
    /*
    1. 스테이지에 도달했으나 아직 클리어하지 못한 플레이어의 수, 스테이지에 도달한 플레이어 수, 실패율, 실패율의 인덱스(스테이지) 배열을 생성
    2. stages를 돌면서 해당 값이 나오면 1씩 증가.(스테이지에 도달했으나 클리어하지 못한 플레이어 수 계산)
    3. 스테이지의 수 만큼 for문을 돌면서 stages.count()를 통해 스테이지에 도달한 플레이어 수를 구하고, 바로 실패율을 계산
    4. 버블 정렬을 통해 반환 값 계산
    */

    class Solution {
        fun solution(N: Int, stages: IntArray): IntArray {
            
            var failArray = Array(N,{0})
            var challengeArray = Array(N,{0})
            var failRateArray = DoubleArray(N,{0.0})

            var failIndexArray = Array(N, {i->i+1})

            // 스테이지에 도달했으나 아직 클리어하지 못한 플레이어의 수
            stages.forEach{
                if(it != N+1) failArray[it-1]++
            }

            // 스테이지에 도달한 플레이어 수, 실패율 계산
            for(i in challengeArray.indices){
                challengeArray[i]=stages.count{it>=i+1}
                failRateArray[i]= failArray[i].toDouble()/challengeArray[i].toDouble()
            }

            // 버블 정렬을 사용.
            // 값의 비교를 통해 내림차순을 하는데, 인덱스 배열도 같이 내림차순 정렬하여 반환
            var temp1 = 0.0
            var temp2 = 0
            for(i in 0..failRateArray.size){
                for(j in 1..failRateArray.size-1){
                    if(failRateArray[j]>failRateArray[j-1]){
                        temp1 = failRateArray[j-1]
                        temp2 = failIndexArray[j-1]
                        failRateArray[j-1]=failRateArray[j]
                        failIndexArray[j-1]=failIndexArray[j]
                        failRateArray[j]=temp1
                        failIndexArray[j]=temp2
                    }
                }
            }
            return failIndexArray.toIntArray()
        }
    }
```