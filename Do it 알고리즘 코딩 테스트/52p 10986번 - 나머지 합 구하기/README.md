```kotlin
fun main() {
    val br = BufferedReader(InputStreamReader(System.`in`))

    val firstLine = StringTokenizer(br.readLine())
    val N = firstLine.nextToken().toInt()
    val M = firstLine.nextToken().toInt()

    val secondLine = StringTokenizer(br.readLine())
    val sumList = LongArray(N+1)
    val remainderList = LongArray(M)

    var count = 0.toLong()

    for(i in 1..N) {
        sumList[i] = secondLine.nextToken().toLong() + sumList[i-1]
        val remainder = (sumList[i]%M).toInt()
        if(remainder == 0) count ++
        remainderList[remainder]++
    }

    for(i in 0 until M) {
        count += (remainderList[i]*(remainderList[i]-1)/2)
    }
    println(count)
}
```