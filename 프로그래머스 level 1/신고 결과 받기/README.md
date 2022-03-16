[신고 결과 받기](https://programmers.co.kr/learn/courses/30/lessons/92334)

결과로 반환할 answer 배열 변수는 id_list의 크기만틈 요소를 가질 수 있도로 수정했다.</br>
idHash라는 해시맵을 만들어서 key 값으로는 id가 value 값으로는 몇 번 신고 당했는지 알 수 있게했다.</br>
resultHash라는 해시맵은 key 값으로는 id, value 값으로는 메일의 수를 담도록 했다.</br>

```kotlin
    class Solution {
        fun solution(id_list: Array<String>, report: Array<String>, k: Int): IntArray {
            
            var answer = IntArray(id_list.size){i -> i}
            var idHash = HashMap<String, Int>()
            var resultHash = HashMap<String, Int>()
            
            // key에 id 설정
            for(i in id_list){
                idHash.put(i, 0)
                resultHash.put(i,0)
            }    

            // 중복제거
            var report = report.distinct().toTypedArray()
            
            // 신고 당한 수를 idHash에 저장
            for(i in report){
                var report_split = i.split(" ")
                var reporter = idHash[report_split[1]]!!.toInt()+1
                idHash.replace(report_split[1], reporter)
            }

            // idHash에서 신고 횟수를 넘긴 해시 값을 새 변수에 저장
            var reporterHash = idHash.filterValues{it >= k}

            // 신고 횟수를 넘긴 id를 저장한 해시 변수 reporterHash를 사용해서 resultHash에 메일의 수 저장.
            for(i in report){
                var report_split = i.split(" ")
                if(reporterHash.containsKey(report_split[1])){
                    var reporter = resultHash[report_split[0]]!!.toInt()+1
                    resultHash.replace(report_split[0], reporter)
                }
            }

            for(i in id_list.indices){
                answer[i]=resultHash[id_list[i]]!!.toInt()
            }
            
            return answer
        }
    }
```
