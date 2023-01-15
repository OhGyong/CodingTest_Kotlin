**평균 구하기** 39p<br/>

```kotlin
fun main() {
    val firstLine = readLine()
    val secondLine = readLine()

    val scoreList = secondLine!!.split(" ").map { it.toInt() }

    var maxScore = 0.0f

    for(i in scoreList){
        if(maxScore < i) maxScore = i.toFloat()
    }

    val newScore = scoreList.map {
        it/maxScore*100
    }

    val newAvg = newScore.sum() / firstLine!!.toFloat()

    println(newAvg)
}
```