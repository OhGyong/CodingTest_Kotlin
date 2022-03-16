[로또의 최고 순위와 최저 순위](https://programmers.co.kr/learn/courses/30/lessons/77484)

```kotlin
    class Solution {

    // lottos 구매한 로또 번호를 담은 배열
    // win_nums 당첨 번호를 담은 배열
    fun solution(lottos: IntArray, win_nums: IntArray): IntArray {
        var answer: IntArray = IntArray(2)

        var syncCount = 0
        var zeroCount = 0


        for(lottosIndex in lottos){
            if(win_nums.contains(lottosIndex)){
                syncCount++
            }else if(lottosIndex == 0){
                zeroCount++
            }
        }

        when(syncCount+zeroCount){
            6-> answer[0]=1
            5-> answer[0]=2
            4-> answer[0]=3
            3-> answer[0]=4
            2-> answer[0]=5
            else-> answer[0]=6
        }

        when(syncCount){
            6-> answer[1]=1
            5-> answer[1]=2
            4-> answer[1]=3
            3-> answer[1]=4
            2-> answer[1]=5
            else-> answer[1]=6
        }

        return answer
    }
}
```