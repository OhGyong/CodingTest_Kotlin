## 매칭 인원 찾기

a, b, c, d 4명의 인원이 있을 때 서로 선택한 인원을 매칭하는 방법<br/>
```kotlin
    fun main(){
        var entryArray = arrayOf("a", "b", "c", "d")
        var matchArray = arrayOf("b", "a", "a", "d")
        
        // 그룹원들이 누구를 선택했는지 저장할 map 변수 선언
        var matchMap =  mutableMapOf(
            "a" to "",
            "b" to "",
            "c" to "",
            "d" to ""
        )
        
        // map에 서로 선택한 사람 저장
        for(i in entryArray.indices){
            matchMap[entryArray[i]]=matchArray[i]
        }
        println(matchMap) // {a=b, b=a, c=a, d=d}
        
        // 매칭 찾기
        for(i in entryArray.indices){
            // 자기 자신을 선택한 사람 제외
            if(entryArray[i]!=matchMap[entryArray[i]]){
                // a부터 시작을 한다고 예를 들면
                // a가 고른사람이 고른사람과 a가 같은지를 확인 ( 매칭 체크 )
                if(matchMap[matchMap[entryArray[i]]] == entryArray[i]){
                    println("${entryArray[i]}  ${matchMap[matchMap[entryArray[i]]]} ${matchMap[entryArray[i]]}")
                    // 1 -> a  a b
                    // 2 -> b  b a
                }
            }
        }
    }
```