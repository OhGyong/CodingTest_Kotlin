[신고 결과 받기](https://programmers.co.kr/learn/courses/30/lessons/92334)

```kotlin
    class Solution {
        fun solution(id_list: Array<String>, report: Array<String>, k: Int): IntArray {
            
            var answer = IntArray(id_list.size){i -> i}
            var idHash = HashMap<String, Int>()
            var resultHash = HashMap<String, Int>()
            
            for(i in id_list){
                idHash.put(i, 0)
                resultHash.put(i,0)
            }    

            var report = report.distinct().toTypedArray()
            
            for(i in report){
                var report_split = i.split(" ")
                var reporter = idHash[report_split[1]]!!.toInt()+1
                idHash.replace(report_split[1], reporter)
            }

            var reporterHash = idHash.filterValues{it >= k}

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
