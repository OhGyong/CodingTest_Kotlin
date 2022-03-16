[직사각형 별찍기](https://programmers.co.kr/learn/courses/30/lessons/12969)

처음에 while문으로 z(Z)가 되었을 때 a(A)로 변경하여 구하려 했는데
아스키 코드를 사용해서 구하는 것이 훨씬 편하다.

```kotlin
    fun main(args: Array<String>) {
        val (a, b) = readLine()!!.split(' ').map(String::toInt)
        // 세로
        for(i in 1..b){
            // 가로
            for(j in 1..a){
                print("*")
            }
            println()
        }
    }
```