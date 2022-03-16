[크레인 인형뽑기 게임](https://programmers.co.kr/learn/courses/30/lessons/64061#)

실패한 코드에서 테스트 1,4,5,6은 통과했지만 나머지가 실패했다.

// 실패
```kotlin
    class Solution {
        fun solution(board: Array<IntArray>, moves: IntArray): Int {
            var answer = 0
            
            // board에서 어디서 뽑을지 알게할 변수
            var positionCheck = Array(board[0].size, {0})

            // 추출한 단어를 담을 문자열 변수
            var pullString = ""

            // 0을 계산해서 어디서 부터 뽑기를 할지 positionCheck를 재선언
            for(i in board){
                for(j in i.indices){
                    if(i[j] == 0) positionCheck[j]++
                }
            }

            // 추출 과정
            moves.forEach{
                if(positionCheck[it-1]<board[0].size) {
                    // 팝하기
                    if(pullString.isNotEmpty() && (pullString[pullString.length-1].toString() == (board[positionCheck[it-1]][it-1]).toString())){
                        answer++
                        pullString = pullString.replace(pullString[pullString.length-1].toString(), "")
                        positionCheck[it-1]++
                    }else{
                        pullString += board[positionCheck[it-1]][it-1]
                        positionCheck[it-1]++
                    }
                }
            }
            return answer*2
        }
    }
```

```kotlin
    import java.util.*

    class Solution {
        fun solution(board: Array<IntArray>, moves: IntArray): Int {
            var answer = 0
            var basket = Stack<Int>()

            moves.forEach {
                for (i in board.indices){
                    if (board[i][it - 1] != 0){
                        if (basket.isNotEmpty() && (basket.peek() == board[i][it - 1])){
                            answer += 2
                            basket.pop()
                        } else {
                            basket.push(board[i][it - 1])
                        }
                        board[i][it - 1] = 0
                        break
                    }
                }
            }
            return answer
        }
    }
```
