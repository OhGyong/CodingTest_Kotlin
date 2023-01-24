```kotlin
fun main() {
    val br = BufferedReader( InputStreamReader(System.`in`) )

    val firstLine = StringTokenizer(br.readLine())
    val N = firstLine.nextToken().toInt()

    var startIndex = 1
    var endIndex = 1
    var count = 1
    var sum = 1

    while (endIndex != N) {
        if(sum == N) {
            count++
            endIndex++
            sum += endIndex
        }
        else if(sum > N) {
            sum-=startIndex
            startIndex++
        }
        else{
            endIndex++
            sum+=endIndex
        }
    }
    println(count)
}
```