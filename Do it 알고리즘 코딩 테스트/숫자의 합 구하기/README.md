**숫자의 합 구하기** 35p<br/>

```kotlin
fun main() {
    val number = readLine()
    val array = readLine()

    var sum = 0

    if (number != null && !array.isNullOrEmpty()) {
        array.map {sum+= it.toString().toInt()}
    }

    println(sum)
}
```