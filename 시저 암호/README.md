[시저 암호](https://programmers.co.kr/learn/courses/30/lessons/12926)

처음에 while문으로 z(Z)가 되었을 때 a(A)로 변경하여 구하려 했는데
아스키 코드를 사용해서 구하는 것이 훨씬 편하다.

```kotlin
   class Solution {
        fun solution(s: String, n: Int): String {
            var answer = ""

            for(i in s){
                if(i.toString() == " "){
                answer += " "  
                }
                // 소문자
                else if(i.toInt()>=97 && i.toInt()<=122){
                    if(i.toInt()+n >122){
                        answer+=(i.toInt()+n-26).toChar()
                    }else{
                        answer+=(i.toInt()+n).toChar()
                    }
                }
                // 대문자
                else if(i.toInt()>=65 && i.toInt()<=90){
                    if(i.toInt()+n >90){
                        answer+=(i.toInt()+n-26).toChar()
                    }else{
                        answer+=(i.toInt()+n).toChar()
                    }
                }
            }
            return answer
        }
    }
```