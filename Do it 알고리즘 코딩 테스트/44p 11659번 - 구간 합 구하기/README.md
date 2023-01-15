```kotlin
fun main() {
    val br = BufferedReader( InputStreamReader(System.`in`) )

    val firstLine = StringTokenizer(br.readLine())
    val numNum = firstLine.nextToken().toInt()
    val repeatNum = firstLine.nextToken().toInt()

    val secondLine = StringTokenizer(br.readLine())
    val arr = arrayListOf<Int>()
    for(i in 0 until numNum) {
        arr.add(secondLine.nextToken().toInt())
    }

    val sumArr = arrayListOf<Int>()
    for(i in 0 until numNum) {
        if(i == 0) {sumArr.add(arr[0])}
        else {sumArr.add(sumArr[i-1] + arr[i])}
    }

    val resultArr = arrayListOf<Int>()
    repeat(repeatNum) {
        val thirdLine = StringTokenizer(br.readLine())
        val i = thirdLine.nextToken().toInt()-2
        val j = thirdLine.nextToken().toInt()-1

        var right = 0
        var left = 0

        if(i >= 0) {left = sumArr[i]}
        if(j >= 0) {right = sumArr[j]}
        resultArr.add(right-left)
    }

    resultArr.map {
        println(it)
    }
}
```