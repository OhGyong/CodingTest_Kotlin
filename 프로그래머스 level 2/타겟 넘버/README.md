[타겟 넘버](https://programmers.co.kr/learn/courses/30/lessons/43165)

모든 요소별로 -1씩 곱해가면서 타겟 값이 생기면 배열에 담아 최종적으로 중복 값을 제거하고 배열의 길이를 반환하면 될 것이라고 생각했는데 완전 탐색 도중 계산하는 부분에서 계속 잘못되었다. 시간이 오래걸려 다른 사람의 풀이를 봤고, dfs를 두 번 호출하면서 위에는 요소에 -를 안한 값 아래는 -를 한 값으로 계산을 쉽게 하였다.

나의 풀이 실패
```kotlin
    import java.util.Arrays

    class Solution {
        var string = ""
        
        fun solution(numbers: IntArray, target: Int): Int {
        var visit = BooleanArray(numbers.size)
            dfs(numbers, 0, visit, target)
            var answer = string.split('A').distinct()
            return answer.slice(0..(answer.size-2)).size
        }
        
        fun dfs(numbers: IntArray, idx: Int, visit: BooleanArray, target: Int){
            visit[idx] = true
            for(i in numbers.indices){
                numbers[i]=-numbers[i]
                if(target == numbers.sum()){
                    string += Arrays.toString(numbers) + "A"
                }
                if(!visit[i]){
                    dfs(numbers, i, visit, target)
                }
            }
        }  
    }
```

나의 풀이 성공
```kotlin
    class Solution {
        
        fun solution(numbers: IntArray, target: Int): Int {
            var cur = numbers[0] // 현재 값
            var answer = 0 // 리턴 값
            answer += dfs(cur, 1, numbers, target)
            answer += dfs(-cur, 1, numbers, target)
            return answer
        }
        
        fun dfs(cur: Int, idx: Int, numbers: IntArray, target: Int): Int{
            if(idx>=numbers.size){
                if(target == cur) return 1
                return 0
            }
            
            var cur1 = cur+numbers[idx]
            var cur2 = cur-numbers[idx]

            // 0 또는 1로 계산된 값들을 반환
            return dfs(cur1, idx+1, numbers, target)+dfs(cur2, idx+1, numbers, target)
        }  
    }
```

다른 사람 풀이
```kotlin
    class Solution {
        var answer = 0
        
        fun solution(numbers: IntArray, target: Int): Int {
            dfs(numbers, target, 0)
            return answer
        }
        
        fun dfs(numbers: IntArray, target: Int, idx: Int){
            if(idx == numbers.size){
                var sum = 0
                for(i in numbers.indices){
                    sum += numbers[i]
                }
                if(sum == target) answer++
                return
            }else{
                dfs(numbers, target, idx+1)
                numbers[idx]*=-1
                dfs(numbers, target, idx+1)
            }
        }  
    }
```