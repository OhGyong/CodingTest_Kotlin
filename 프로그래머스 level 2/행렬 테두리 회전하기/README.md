[행렬 테두리 회전하기](https://programmers.co.kr/learn/courses/30/lessons/77485)

행렬 matrix를 만들어서 회전 목록 queries를 통해 값을 변경했다.<br/>
문제에서 시계방향으로 회전을 한다고 나와있는데 시계 방향으로 회전하도록 구현을 하면 우측 상단 꼭짓점 값이 변하기 때문에 시계 역방향으로 회전을 하게 하여 좌측 상단 꼭짓점(최소값)부터 아래로 값을 바꿔가면서 계산을 했다.

나의 풀이
```kotlin
    class Solution {
        fun solution(rows: Int, columns: Int, queries: Array<IntArray>): IntArray {
            val matrix = Array(rows, {i-> Array(columns, {i*columns+it+1})})
            return IntArray(queries.size, {rotationMatrix(queries[it], matrix)})
        }
        
        fun rotationMatrix(queries: IntArray, matrix: Array<Array<Int>>): Int{
            var x1 = queries[1]-1
            var y1 = queries[0]-1
            var x2 = queries[3]-1
            var y2 = queries[2]-1

            var min = matrix[y1][x1] // 최소값 저장 변수
            var tmp = min // 마지막에 최소값 변경 위한 변수

            // 왼쪽 회전
            for(i in y1 until y2){
                matrix[i][x1] = matrix[i+1][x1]
                min = min.coerceAtMost(matrix[i][x1]) // 최소값 저장
            }

            // 아래쪽 회전
            for(i in x1 until x2){
                matrix[y2][i] = matrix[y2][i+1]
                min = min.coerceAtMost(matrix[y2][i])
            }

            // 오른쪽 회전
            for(i in y2 downTo y1+1){
                matrix[i][x2] = matrix[i-1][x2]
                min = min.coerceAtMost(matrix[i][x2])
            }

            // 위 회전
            for(i in x2 downTo x1+1){
                matrix[y1][i] = matrix[y1][i-1]
                min = min.coerceAtMost(matrix[y1][i])
            }
            matrix[y1][x1+1] = tmp // 회전하고 한칸 앞은 최소값의 자리
            return min
        }
    }
```