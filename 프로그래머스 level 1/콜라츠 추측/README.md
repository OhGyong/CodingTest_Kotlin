[콜라츠 추측](https://programmers.co.kr/learn/courses/30/lessons/12943)

나의 풀이
```kotlin
    class Solution {
        fun solution(num: Int): Int {
            var count=0
            var number:Long=num.toLong()
            while(number!=1.toLong()){
                if(count==500){
                    count=-1
                    break
                }
                if(number%2.toLong()==0.toLong()) number = number/2.toLong() 
                else number=number*3 + 1
                count++
        }
            return count
        }
    }
```