[오픈채팅방](https://programmers.co.kr/learn/courses/30/lessons/42888#)

해시를 이용해서 Enter인 경우를 체크해서 key=id, value=name으로 설정했다.<br/>
key는 중복이 안되기 때문에 나중에 Enter로 들어온 id의 name이 바뀌었을때 자동으로 name이 변경된다.<br/>
Change가 나올때는 해당 key값을 찾아서 value를 변경시켰다.
<br/><br/>

해시의 key, value 세팅이 끝나면 record를 돌면서 해시에서 id에 맞는 name을 꺼내서 문자열 리스트에 추가 시켜주고 반환했다.

나의 풀이
```kotlin
    class Solution {
        fun solution(record: Array<String>): Array<String> {
            var map = mutableMapOf<String, String>()
            record.forEach{
                if((it.split(" "))[0] == "Enter"){
                    map.put((it.split(" "))[1], (it.split(" "))[2])
                }
                else if((it.split(" "))[0] == "Change"){
                    map[(it.split(" "))[1]] = (it.split(" "))[2]
                }
            }

            var answer = mutableListOf<String>()
            record.forEach{
                if((it.split(" "))[0] == "Enter"){
                    answer.add(map[(it.split(" "))[1]] + "님이 들어왔습니다.")
                }
                else if((it.split(" "))[0] == "Leave"){
                    answer.add(map[(it.split(" "))[1]] + "님이 나갔습니다.")
                }
            }
            return answer.toTypedArray()
        }
    }
```