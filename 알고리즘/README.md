## 완전탐색(Exhaustive Search)
완전탐색은 가능한 모든 경우의 수를 모두 확인하면서 정답을 찾는 방법이다. 무식하게 하는 방식이라는 의미로 **Brute Force**라고도 부른다.<br/>
완전탐색의 기법을 활용한 방법으로 `Brute Force 기법`, `백트래킹`, `순열`, `재귀함수`, `비트 마스크`, `DFS/BFS` 가 있다.

### DFS(깊이 우선 탐색)
루트 노드에서 시작해서 다음 분기로 넘어가기 전에 해당 분기를 완벽하게 탐색하는 방법이다.<br/>
자기 자신을 호출하는 순환 알고리즘의 형태를 지니며, 이 알고리즘을 구현할 때 어떤 노드를 방문했었는지 여부를 반드시 검사해야 한다.

```kotlin
    fun main(){
        var numbers = intArrayOf(1,2,3,4,5)
        var visit = BooleanArray(5)
        dfs(numbers, 0, visit)
    }

    fun dfs(numbers: IntArray, idx: Int, visit: BooleanArray){
        visit[idx] = true
        println(Arrays.toString(visit))
        for(i in numbers.indices){
            if(!visit[i]){
                dfs(numbers, i, visit)  
            } 
        }
    }
```
![image](https://user-images.githubusercontent.com/52282493/158790054-7d6b9c4c-ea6f-4528-9343-99d451fb9b24.png)