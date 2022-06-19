[괄호 변환](https://programmers.co.kr/learn/courses/30/lessons/60058)

나의 풀이 
```kotlin
    class Solution {
        fun solution(p: String): String {
            return solveString(p)
        }
        
        // 문자열 구하기
        fun solveString(p: String) : String {
            var answer = ""
            var leftCount = 0
            var rightCount = 0   
            var u = ""
            var v = ""

            if(p.isNotBlank()){
                for(i in 0..p.length-1){

                    if(p[i].equals('(')) leftCount++
                    else rightCount++

                    if(leftCount == rightCount){
                        u = p.substring(0, i+1)
                        v = p.substring(i+1)
                        break
                    }
                }

                if(isRightString(u)){
                    answer = u + solveString(v)
                }else{
                    var tmp = ""

                    u = u.substring(1, u.length-1)
                    for(i in 0..u.length-1){
                        if(u[i].equals('(')) tmp += ")"
                        else tmp += "("
                    }
                    answer = "(${solveString(v)})$tmp"
                }
                return answer
            }
            return ""
        }

        // 올바른 문자열인지 확인
        fun isRightString(u: String): Boolean {
            var leftCount = 0
            var rightCount = 0
            var isRight = false

            for(i in 0..u.length-1){
                if(u[i].equals('(')) leftCount++
                else rightCount++

                if(leftCount<rightCount){
                    isRight=false
                    break
                }
                else isRight=true
            }
            return isRight
        }
    }
```