### 투 포인터 사용
```kotlin
fun main() {
    val br = BufferedReader( InputStreamReader(System.`in`) )

    val N = StringTokenizer(br.readLine()).nextToken().toInt()
    val M = StringTokenizer(br.readLine()).nextToken().toInt()

    val thirdLine = StringTokenizer(br.readLine())

    val array = arrayListOf<Int>()

    repeat(N) {
        array.add(thirdLine.nextToken().toInt())
    }
    array.sort()

    var startIndex = 0
    var endIndex = N-1
    var count = 0

    while (startIndex<endIndex) {
        if (array[startIndex] + array[endIndex] == M) {
            count++
            startIndex++
            endIndex--
        } else if (array[startIndex] + array[endIndex] < M) {
            startIndex++
        }
        else {
            endIndex--
        }
    }

    println(count)
}
```

---

### 이중 for문
```kotlin
fun main() {
    val br = BufferedReader( InputStreamReader(System.`in`) )

    val N = StringTokenizer(br.readLine()).nextToken().toInt()
    val M = StringTokenizer(br.readLine()).nextToken().toInt()

    val thirdLine = StringTokenizer(br.readLine())

    val array = arrayListOf<Int>()

    repeat(N) {
        array.add(thirdLine.nextToken().toInt())
    }

    var count = 0
    for(i in 0 until N-1) {
        for(j in i+1 until N) {
            if(array[i]+array[j] == M){
                count++
            }
        }
    }

    println(count)
}
```