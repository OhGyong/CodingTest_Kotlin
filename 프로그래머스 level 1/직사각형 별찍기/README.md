[직사각형 별찍기](https://programmers.co.kr/learn/courses/30/lessons/12969)

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