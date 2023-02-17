```kotlin
fun main() {
    val br = BufferedReader( InputStreamReader(System.`in`) )

    val N = StringTokenizer(br.readLine()).nextToken().toInt()
    val secondLine = StringTokenizer(br.readLine())
    val list = arrayListOf<Long>()

    repeat(N) { list.add(secondLine.nextToken().toLong()) }
    list.sort()

    var count = 0

    list.forEachIndexed {targetIndex, target ->
        var startIndex = 0
        var endIndex = list.lastIndex

        while(startIndex < endIndex) {
            val sum = list[startIndex] + list[endIndex]

            if(sum == target) {
                if(targetIndex==startIndex){
                    startIndex++
                } else if(targetIndex==endIndex ){
                    endIndex--
                } else {
                    count++
                    break
                }
            } else if (sum < target) {
                startIndex++
            } else {
                endIndex--
            }
        }
    }

    println(count)
}
```