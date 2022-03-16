[키패드 누르기](https://programmers.co.kr/learn/courses/30/lessons/67256#)

키패드에서 1은 [0,0], 2는 [0,1], 4는 [1,0]으로 가로 방향이 y축, 세로 방향이 x축이라고 생각하고 좌표를 통해 거리 계산을 통해 해결하였다.

```kotlin
    import kotlin.math.abs

    class Solution {
        fun solution(numbers: IntArray, hand: String): String {
            var answer = ""
            
            // 왼손, 오른손의 첫 위치
            var lHandCoor = intArrayOf(3,0)
            var rHandCoor = intArrayOf(3,2)
            
            // 거리 계산에 이용할 변수
            var lToTarget = 0
            var rToTarget = 0
            
            for(i in numbers){
                var targetCoor = intArrayOf()
                
                if(i == 0){
                    // *, #은 계산을 안하니 0의 위치만 따로 계산
                    targetCoor = intArrayOf(3,1)
                }else{
                    // 1~9까지 좌표 계산
                    targetCoor = intArrayOf((i-1)/3, (i-1)%3)
                }
                
                // y좌표가 0인 곳(1,4,7)
                if(targetCoor[1]==0){
                    answer += "L"
                    lHandCoor = targetCoor 
                }
                // y좌표가 2인 곳(3,6,9)
                else if(targetCoor[1]==2){
                    answer += "R"
                    rHandCoor = targetCoor 
                }
                else{
                    // 타켓과 왼손 위치까지의 거리 계산
                    lToTarget = abs(lHandCoor[0] - targetCoor[0]) + abs(lHandCoor[1] - targetCoor[1])
                    // 타켓과 오른손 위치까지의 거리 계산
                    rToTarget = abs(rHandCoor[0] - targetCoor[0]) + abs(rHandCoor[1] - targetCoor[1])
                    
                    // 왼손 위치가 더 가까운경우
                    if(lToTarget < rToTarget){
                        answer += "L"
                        lHandCoor = targetCoor 
                    }
                    // 오른손 위치가 더 가까운 경우
                    else if(lToTarget > rToTarget){
                        answer += "R"
                        rHandCoor = targetCoor
                    }
                    // 왼손 오른손 거리가 같은 경우
                    else{
                        if(hand == "left"){
                            answer += "L"
                            lHandCoor = targetCoor
                        } 
                        else{
                            answer += "R"
                            rHandCoor = targetCoor
                        } 
                    }
                }
            }
            return answer
        }
    }
```