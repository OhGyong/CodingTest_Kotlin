[모의고사](https://programmers.co.kr/learn/courses/30/lessons/42840)

이번 문제의 핵심은 person1, person2, person3라는 크기가 다른 세개의 배열에서 나머지 연산자(%)를 통해 answers 배열과 인덱스 비교를 해주는 거라고 생각한다.

나의 풀이
```kotlin
    class Solution {
        fun solution(answers: IntArray): IntArray {
            
            var person1 = arrayOf(1,2,3,4,5)
            var person2 = arrayOf(2,1,2,3,2,4,2,5)
            var person3 = arrayOf(3,3,1,1,2,2,4,4,5,5)
            
            var person1Answers = 0
            var person2Answers = 0
            var person3Answers = 0
            
            
            for(i in answers.indices){
                if(answers[i] == person1[i%person1.size]) person1Answers++
                if(answers[i] == person2[i%person2.size]) person2Answers++
                if(answers[i] == person3[i%person3.size]) person3Answers++
            }
            
            if(person1Answers == person2Answers && person2Answers==person3Answers){
                var answer = intArrayOf(0,0,0)
                answer[0]=1
                answer[1]=2
                answer[2]=3
                return answer
                
            }else if(person1Answers>person2Answers && person1Answers>person3Answers){
                var answer = intArrayOf(1)
                return answer
            }else if(person2Answers>person1Answers && person2Answers>person3Answers){
                var answer = intArrayOf(2)
                return answer
            }else if(person3Answers>person2Answers && person3Answers>person1Answers){
                var answer = intArrayOf(3)
                return answer
            }else if(person1Answers==person2Answers && person1Answers>person3Answers){
                var answer = intArrayOf(1,2)
                return answer
            }else if(person1Answers==person3Answers && person1Answers>person2Answers){
                var answer = intArrayOf(1,3)
                return answer
            }else if(person2Answers==person3Answers && person2Answers>person1Answers){
                var answer = intArrayOf(2,3)
                return answer
            }
            
            var answer = intArrayOf(0)
            return answer
        }
    }
```

다른 사람 풀이
```kotlin
    class Solution {
        fun solution(answers: IntArray): IntArray {
            var supo1 = intArrayOf(1,2,3,4,5)
            var supo2 = intArrayOf(2,1,2,3,2,4,2,5)
            var supo3 = intArrayOf(3,3,1,1,2,2,4,4,5,5)
            var x = 0; var y = 0; var z = 0

            var map = mutableMapOf<Int,Int>(Pair(1,0),Pair(2,0),Pair(3,0))
            for(i in answers) {
                if(i == supo1[x]) map.put(1,map[1]!! + 1)
                if(i == supo2[y]) map.put(2,map[2]!! + 1)
                if(i == supo3[z]) map.put(3,map[3]!! + 1)
                x = if(x < 4) x + 1 else 0
                y = if(y < 7) y + 1 else 0
                z = if(z < 9) z + 1 else 0
            }

            var max = map.maxBy({it.value})?.value
            for(i in 1..map.size) if(map[i] != max) map.remove(i)
            var answer = map.toList().sortedWith(compareBy({it.second})).toMap().keys.toIntArray()

            return answer
        }
    }
```