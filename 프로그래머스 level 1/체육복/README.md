[체육복](https://programmers.co.kr/learn/courses/30/lessons/42862)

```kotlin
    /*
    1. 전체학생 n에 따른 전체학생 배열을 1의 값을 가진채로 생성
    2. 도난당한 배열 lost를 통해 전체학생 배열에서 해당하는 학생을 1 감소
    3. 여분이 있는 학생 배열 reserve를 통해 전체학생 배열에서 해당하는 학생을 1 증가
    4. 전체 학생 배열 돌면서 1이면 넘어가고 0일때 앞 뒤로 조회해서 2가있으면 1을 빼서 넘겨주는 방식으로
    5. 전체 학생 배열에서 1인 값을 카운트
    */

    class Solution {
        fun solution(n: Int, lost: IntArray, reserve: IntArray): Int {
            var answer = 0
            
            var totalStudent = Array(n, {1})
        
            lost.forEach{ totalStudent[it-1] += -1  }
            reserve.forEach{ totalStudent[it-1]++ }

            for(i in totalStudent.indices){
                // 도난 당한 학생이면
                if(totalStudent[i]==0){
                    // 앞 학생이 여분이 있는 경우
                    if(i!=0 && totalStudent[i-1]==2){
                        totalStudent[i-1]=1
                        totalStudent[i]=1
                    }
                    // 뒤 학생이 여분이 있는 경우
                    else if(i!=(n-1) && totalStudent[i+1]==2){
                        totalStudent[i+1]=1
                        totalStudent[i]=1
                    }
                    // 맨 앞 학생이 도난 당했을 때
                    else if(i==0 && totalStudent[i+1]==2){
                        totalStudent[i+1]=1
                        totalStudent[i]=1
                    }
                    // 맨 뒤 학생이 도난 당했을 때
                    else if(i==(n-1) && totalStudent[i-1]==2){
                        totalStudent[i+1]=1
                        totalStudent[i]=1
                    }
                }
            }
            answer = totalStudent.count(){ it >= 1}
            return answer
        }
    }
```