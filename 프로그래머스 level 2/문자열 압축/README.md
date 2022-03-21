[문자열 압축](https://programmers.co.kr/learn/courses/30/lessons/60057)

문자열을 압축하면서 최소 길이의 문자열을 찾아야 했기에 완전탐색을 해야 한다고 생각했다.<br/>
루프문 범위 외의 길이를 저장할 변수를 만들어두고, 첫번째 루프문은 압축 단위로 한 뒤에 그 안의 루프문을 통해 압축한 문자열을 만들어서 minOf를 통해 최소 길이를 찾아 반환하도록 하였다.

나의 풀이
```kotlin
    class Solution {
        fun solution(s: String): Int {
            var min = s.length // 반환해줄 최소 길이
        
            // 압축 단위 설정
            for(i in 1..s.length){
                var finalStr = "" // 압축으로 변한 최종 문자열
                var count = 2 // 압축된 횟수 카운트(1은 제외)
                var isCP = false // 압축되서 변경되었는지 확인
                var curStr = s.substring(0, i) // 현재 분할 된 단어
                var sumStr = "" // 현재 분할 된 단어 + 다음 분할 된 단어

                // 분할 단위 기준으로 압축시도
                var j = i

                // 압축 단위가 문자열 길이 넘어가면 검사 안해도 됨.(for문이면 index에러 발생 하니까 while로)
                while(j+i<=s.length){
                    var nextStr = s.substring(j, j+i) // 다음 분할 된 단어 (j 인덱스 부터 그 다음 단위까지)
                    // 현재 분할 된 단어와 다음 분활 된 단어가 같으면 sumStr에 압축한 문자열을 추가
                    if(curStr == nextStr){
                        sumStr = count.toString() + curStr
                        count++
                        isCP=true
                    }else{
                        // 압축된 단어가 있으면 압축된 문자열을 저장했던 sumStr을 추가
                        if(isCP) finalStr += sumStr
                        // 없으면 현재 단어를 추가
                        else finalStr += curStr

                        // 다음 while문 때 다시 검사해야 하므로 초기화
                        isCP = false
                        curStr = nextStr
                        count = 2
                        sumStr = ""
                    }
                    println("$j $i")
                    j += i // 압축한 만큼 증가
                    println("$j $i")
                }
                // sumStr이 빈 경우에는 while문에서 초기화 하다가 탈출한 경우이므로 뒤의 나머지 부분을 다 붙여준다.
                // while문이 끝날 때 j+i가 되기 때문에 나머지 부분은 j-i부터 s.length가 된다.
                if(sumStr.isEmpty()) finalStr += s.substring(j-i, s.length)
                // sumStr에 값이 있는 경우는 압축을 하고 while문에서 탈출한 것이기 때문에 
                // 압축한 만큼 증가된 j 부터 나머지 부분을 붙여주면 된다.
                else finalStr += (sumStr + s.substring(j, s.length))

                min = minOf(min, finalStr.length)
            }
            return min
        }
    }
```