[가장 많이 받은 선물](https://school.programmers.co.kr/learn/courses/30/lessons/258712)

나의 풀이
```kotlin
    class Solution {
        fun solution(friends: Array<String>, gifts: Array<String>): Int {
            var answer: Int = 0
    
            val giftTimesMap = HashMap<String, HashMap<String, Int>>() // 누가 누구에게 선물을 얼마큼 줬는지
            val giftScoreMap = HashMap<String, Int>() // 선물 지수
            val nextMonthMap = HashMap<String, Int>() // 다음 달 받을 양
    
            friends.forEach {
                giftTimesMap[it] = HashMap()
                giftScoreMap[it] = 0
                nextMonthMap[it] = 0
            }
    
            /**
             * 준 사람은 +1, 받은 사람은 -1
             */
            gifts.forEach {
                val giver = it.split(" ")[0]
                val receiver = it.split(" ")[1]
    
                giftTimesMap[giver]!![receiver] = giftTimesMap[giver]!!.getOrDefault(receiver, 0) + 1
                giftTimesMap[receiver]!![giver] = giftTimesMap[receiver]!!.getOrDefault(giver, 0) - 1
            }
    
            // giftTimesMap을 앞에서 돌면서 + 값 찾기
            friends.forEach { member->
                // 선물을 주고 받았을 때 0보다 큰 것은 더 많이 줬다는 뜻
                giftTimesMap[member]!!.values.forEach {giftTimes->
                    if(giftTimes > 0) {
                        // 선물 더 많이 준 사람 다음 달 선물 +1
                        nextMonthMap[member]=nextMonthMap[member]!! + 1
                    }
                }
                giftScoreMap[member] = giftTimesMap[member]!!.values.sum() // 선물 지수 계산
            }
    
            // 선물 준 사람 받은 사람 중복 안되게 Index 접근
            for(giverPoint in friends.indices) {
                val giver = friends[giverPoint]
                for(receiverPoint in giverPoint+1 until friends.size) {
                    val receiver = friends[receiverPoint]
    
                    // 두 사람이 선물을 주고받은 기록이 없는 경우
                    if(!giftTimesMap[giver]!!.containsKey(receiver)) {
                        compareGiftScore(giftScoreMap, nextMonthMap, giver, receiver)
                    }
                    // 기록이 있는 경우 주고받은 수가 같다면
                    else {
                        if(giftTimesMap[giver]!![receiver]!! == 0 && giftTimesMap[receiver]!![giver]!! == 0) {
                            compareGiftScore(giftScoreMap, nextMonthMap, giver, receiver)
                        }
                    }
                }
            }
    
            answer = nextMonthMap.values.maxOrNull()!! // 다음 달 받는 값중 최대 값 추출
    
            return answer
        }
    
        /**
         * 선물 지수 비교 후 더 큰 사람 다음 달 선물 +1
         */
        fun compareGiftScore(
            giftScoreMap: HashMap<String, Int>,
            nextMonthMap: HashMap<String, Int>,
            giver: String,
            receiver: String
        ) {
            if(giftScoreMap[giver]!!>giftScoreMap[receiver]!!) {
                nextMonthMap[giver]=nextMonthMap[giver]!! + 1
            } else if(giftScoreMap[giver]!!<giftScoreMap[receiver]!!) {
                nextMonthMap[receiver]=nextMonthMap[receiver]!! + 1
            }
        }
    }
```