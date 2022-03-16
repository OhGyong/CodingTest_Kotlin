[소수 만들기](https://programmers.co.kr/learn/courses/30/lessons/12977)

나의 풀이
```kotlin
    class Solution {
        fun solution(nums: IntArray): Int {
            var answer = 0
            
            for(i in 0 until nums.size-2){
                for(j in i+1 until nums.size-1){
                    for(k in j+1 until nums.size){
                        var primeNumber =  nums[i] + nums[j] + nums[k]
                        var flag = true
                        for(l in 2 until primeNumber){
                            if(primeNumber%l == 0){
                                flag = false
                                break
                            }
                        }
                        if(flag == true) answer++
                    }
                }
            }
            
            return answer
        }
    }
```