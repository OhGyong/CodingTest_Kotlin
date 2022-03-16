[2016년](https://programmers.co.kr/learn/courses/30/lessons/12901)

나의 풀이
```kotlin
    import java.text.SimpleDateFormat  
    import java.util.*  
    
    class Solution {  
        fun solution(a: Int, b: Int): String {  
            val calendar = Calendar.getInstance()  
            calendar.set(2016, a-1, b)  
            return SimpleDateFormat("EEE", Locale.ENGLISH).format(calendar.timeInMillis).toUpperCase()  
        }  
    }
```