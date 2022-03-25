[피보나치 수](https://programmers.co.kr/learn/courses/30/lessons/12945)

처음에 피보나치 수를 구하는 재귀함수를 구현을 했었는데 채점 중 시간 초과가 발생하는 문제가 있었다.<br/>
재귀로 구하는 경우 시간 복잡도가 O(2^n)이기 때문에 이 문제를 해결해야 했다.<br/>
배열을 만들고 for문을 통해 n=3 부터 피보나치 수를 계산하여 배열에 저장하는 방식을 통해 시간 문제를 해결할 수 있었다.



나의 풀이
```kotlin
    class Solution {
        fun solution(n: Int): Int {
            if(n==2) return 2
            var answer = IntArray(n+1){1}
            for(i in 3..n){
                answer[i]=(answer[i-2]+answer[i-1])%1234567
            }
            return answer[n]
        }
    }
```