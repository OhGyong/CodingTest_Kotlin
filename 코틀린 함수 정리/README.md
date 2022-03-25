## Array
배열을 생성한 순간에 사이즈는 고정이 되고, 원소 삭제나 추가 등을 할 수 없다.(plus를 사용하면 추가 가능)</br>


### 배열 생성

1. arrayOf()
arrayOf()를 사용하여 값을 직접 할당할 수 있다.


```kotlin
    // 배열에 저장되는 요소의 타입을 제네릭으로 지정하는 경우
    var arrayInt = arrayOf<Int>(1, 2, 3)
    var arrayString = arrayOf<String>("hello", "world")

    // 함수를 사용하여 지정하는 경우
    var arrayInt = intArrayOf(1, 2, 3)
    var array = arrayOf(1, 2, "HelloWorld")
```

2. Array()
Array 생성자를 사용하여 배열을 생성할 수 있다.</br>
arrayOf와 마찬가지로 제네릭이나 함수의 사용이 가능하다.

```kotlin
    // Array(배열 크기, {값})
    var array1 = Array(5, {0}) // [0, 0, 0, 0, 0]
    var array2 = Array(5, {i -> i+1}) // [1, 2, 3, 4, 5], 람다식으로 선언 가능
    var array3 = IntArray(5) // [0, 0, 0, 0, 0]
```

### 배열 출력

java.util.Arrays을 호출하여 배열을 출력할 수 있다.

```kotlin

    // 1차원 배열
    var arrayOf = arrayOf("Hello", "world")
    println(Arrays.toString(arrayOf)) // [Hello, world]

    // 2차원 배열
    var array = arrayOf(arrayOf(1,2,3), arrayOf(4,5,6), arrayOf(7,8,9))
    println(array.contentDeepToString()) // [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
```

### 배열 크기

```kotlin
    var array = IntArray(5)
	array.size // 5
```

### 요소 추가

Array.plus()를 통해 배열에 요소를 추가할 수 있다.

```kotlin
    // 변수에 덮어쓰기 해줘야한다.
    var array = arrayOf(1, 2, 3)
    println(Arrays.toString(array.plus(4))) // [1, 2, 3, 4]
    println(Arrays.toString(array)) // [1, 2, 3]

    array = array.plus(4)
    println(Arrays.toString(array)) // [1, 2, 3, 4]
```

### 요소 찾기

contains() 함수를 사용하면 배열에 해당 요소의 존재 유무에 따라 true, false를 반환한다.

```kotlin
    var array = arrayOf(1, 2, 3)
    println(array.contains(2)) // true
```

### 범위 자르기

sliceArray()를 사용하면 Array의 원하는 범위 만큼을 배열로 반환해준다. → slice()를 사용해도 똑같은 것으로 확인.

```kotlin
    var array = arrayOf(0,1,2,3,4,5)
    println(Arrays.toString(array.sliceArray(1..3))) // [1, 2, 3]
```

<br/><br/>

---
## 컬렉션 함수

### filter
특정 조건을 만족하는 요소로 이루어진 새로운 컬렉션을 반환한다.

```kotlin
    var array = arrayOf(1, 2, 3, 4, 5)
    println(array.filter{ it > 2 }) // [3, 4, 5]
```

### map
원소를 원하는 형태로 변환하여 새로운 컬렉션을 반환한다.

```kotlin
    var array = arrayOf(1, 2, 3, 4, 5)
    println(array.map{it->it*it}) // [1, 4, 9, 16, 25]
```

Key와 Value를 쌍으로 데이터를 저장하는 방식의 함수로 Key는 중복이 불가능하다.

```kotlin
    var map =  mapOf(
        "치킨" to 15000,
        "피자" to 11000,
        "파스타" to 5000
    )
    println(map) // {치킨=15000, 피자=11000, 파스타=5000}
    println(map.keys) // [치킨, 피자, 파스타]
    println(map.values) // [15000, 11000, 5000]

    /**
    * Pair() 라는 컬렉션 함수는 map 처럼 key와 value로 이루어진 형태이기 때문에 map에 데이터를 넣을때 사용할 수 있다.
    */
    var mapWithPair = mapOf( Pair("치킨", 15000), Pair("피자", 11000), Pair("파스타", 5000))
    println(mapWithPair) // {치킨=15000, 피자=11000, 파스타=5000}
```

### groupBy
특정 조건을 만족하는 그룹으로 나눈 컬렉션을 반환한다.

```kotlin
    val array1 = arrayOf("muzi", "frodo", "apeach", "neo")
    var array2 = arrayOf("muzi frodo","apeach frodo","frodo neo","muzi neo","apeach muzi")

    var array3 = array2.map{it.split(" ")}
	println(array3) // [[muzi, frodo], [apeach, frodo], [frodo, neo], [muzi, neo], [apeach, muzi]]
   	
    var array4 = array3.groupBy{it[1]}
    println(array4) // {frodo=[[muzi, frodo], [apeach, frodo]], neo=[[frodo, neo], [muzi, neo]], muzi=[[apeach, muzi]]}

    var array = arrayOf(1, 2, 3, 4)
    println(array.groupBy{2}) // {2=[1, 2, 3, 4]}
```

### distinct
원소의 중복을 제거하여 새로운 컬렉션을 반환한다.

```kotlin
    var array = arrayOf(1, 2, 3, 4, 1, 2, 5, 6, 7)
    println(array.distinct()) // [1, 2, 3, 4, 5, 6, 7]
```

### flatten
컬렉션 안에 컬렉션이 들어있는 중첩 컬렉션을 하나의 컬렉션으로 반환한다.

```kotlin
    var array = arrayOf(arrayOf(1,2,3), arrayOf(4,5,6), arrayOf(7,8,9))
    println(array.contentDeepToString()) // [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
    println(array.flatten()) // [1, 2, 3, 4, 5, 6, 7, 8, 9]
```

### groupingBy
eachCount()를 통해 컬렉션 안에서 특정 조건에 해당하는 원소의 개수를 구할 때 사용된다.

```kotlin
    var array = arrayOf(1, 2, 3, 4, 5, 1, 1, 3)
    println(array.groupingBy{it}.eachCount()) // {1=3, 2=1, 3=2, 4=1, 5=1}

    var array = arrayOf("a", "b", "c", "a", "a", "b")
    println(array.groupingBy{it}.eachCount()) // {a=3, b=2, c=1}
```

### fold, foldIndexed
fold()를 사용하면 람다식을 순서대로 적용한 결과를 얻을 수 있다.</br>
foldIndexed()는 람다식에서 인덱스와 값을 동시에 인자로 받을 수 있다.

```kotlin
	val array = arrayOf(1,2,3,4)
    
    // fold(i)에서 i는 twiceTotal의 초기값, element는 요소
    val useFold1 = array.fold(0){ twiceTotal, element -> twiceTotal + element*2}
    val useFold2 = array.fold(5){ twiceTotal, element -> twiceTotal + element*2}
    
    println(useFold1) // 20 -> 0+2+4+6+8
    println(useFold2) // 25 -> 5+2+4+6+8
    
    
    // foldIndexed(i)에서 i는 result의 초기값, idx는 인덱스, element는 요소
    val useFoldIndexed1 = array.foldIndexed(3){ idx, result, element ->
        if(idx == 3) result*4
        else result
    }
    
    val useFoldIndexed2 = array.foldIndexed(0){ idx, result, element ->
    	if(idx%2 == 1) result+element
        else result
    }
    
    println(useFoldIndexed1) // 12 -> 3*4
    println(useFoldIndexed2) // 6 -> idx가 1,3일때 = element는 2와 4,즉 2+4
```

### 컬렉션 정렬

```kotlin
    // sortBy{}는 컬렉션 내에 여러 객체가 있을 때 그 객체를 기준으로 해서 정렬을 할 수 있다. 
    var array = arrayOf("cd", "ac", "dz", "eq", "bx")
    var newArray = array.also{it.sortBy{it[0]}}
    println(Arrays.toString(newArray)) // [ac, bx, cd, dz, eq]

    // sortedArray()는 오름차순으로 정렬된 새로운 배열을 반환한다. 역배열은 Descending()을 붙인다.
    var array = arrayOf(3,4,2,1,5,7)
	var newS1 = array.sortedArray()
    var newS2 = array.sortedArrayDescending()
    println(Arrays.toString(newS1)) // [1, 2, 3, 4, 5, 7]
    println(Arrays.toString(newS2)) // [7, 5, 4, 3, 2, 1]
```

### 컬렉션 반복
컬렉션에서 forEach{} 문을 쓰면 for문을 쓰지 않고도 값을 구할 수 있다.<br/>
만약 익덱스 정보가 필요하다면 forEachIndexed를 사용하면 된다.
```kotlin
    var array = arrayOf("a", "b", "c", "d")
    array.forEach{print("$it ")} // a b c d 
    array.forEachIndexed{index, it -> print("$index $it | ")} // 0 a | 1 b | 2 c | 3 d | 
```

<br/><br/>

---
## :: (더블 콜론)
변수앞에 ::을 명시하면 변수를 객체로 액세스하여 객체에 대한 속성을 참조하게 된다.</br>

```kotlin
    var array1 = arrayOf(1, 2, 3, 4, 5)
    var array2 = arrayOf(1, 2, 8, 6, 5)
    println(array1.filter(array2::contains)) // [1, 2, 5]
```


<br/><br/>

---
## 연산자 함수

### plus
숫자 데이터에 plus()를 하면 연산이 되고, 문자 데이터에 plus()를 하면 결합이 된다.

```kotlin

    var a="Hello"
    var b="World"
    println(a.plus(b)) // HelloWorld
    
    var c=1
    var d=2
    println(c.plus(d)) // 3

```

<br/><br/>

---
## 문자열

### 대문자, 소문자 전환
toUpperCase, toLowerCase를 사용하여 전환을 할 수 있다.

```kotlin
   var string = "QWER asdf"	
   println(string.toLowerCase()) // qwer asdf
   println(string.toUpperCase()) // QWER ASDF
```

### replace
코틀린에는 replaceAll이 없지만 replace로 그 기능을 대체할 수 있다.
replace는 특정 문자열을 지정한 문자열로 바꿔준다.

```kotlin
   var string = "Hello World"	
   println(string.replace("Hello", "Hi")) // Hi World
```

### slice
문자열에서 부분 문자열을 추출할 때 사용한다.

```kotlin
   var string = "Hello World"	
   println(string.slice(0..4)) // Hello
```

### substring
slice와 유사하게 부분 문자열을 추출할 때 사용한다.</br>
slice는 범위 지정을 반드시 해야하지만 substring은 입력값을 하나만 넣으면 자동으로 문자열의 끝까지 추출한다.

```kotlin
   var string = "Hello World"
   println(string.substring(0..4)) // Hello
   println(string.substring(2)) // llo World
   println(string.substring(string.length-1)) // d
```

<br/><br/>

---
## 정규식
toRegex() 함수를 사용하여 코틀린에서 정규식을 사용할 수 있다.</br>
**신규 아이디 추천**문제를 풀 때 사용한 정규식으로 참고해서 사용하자.

### 알파벳 소문자, 숫자, -(빼기), _(밑줄), .(마침표)를 제외한 모든 문자를 제거하기
[^ ]를 사용하면 [] 범위의 문자 집합을 제외한 것을 찾는다.

```kotlin
   var answer = "...!@BaT#*..y.abcdefghijklm"	
   answer = answer.replace("[^a-z0-9_.-]".toRegex(), "")
   println(answer) // ...a..y.abcdefghijklm
```

### 문자열에 2번 이상 반복되는 문자를 하나의 문자로 치환하기
regex{n, }은 regex라는 표현식이 n번 이상 일치되는 것을 찾는다.

```kotlin
   var answer = "...!@BaT#*..y.abcdefghijklm"	
   answer = answer.replace("[.]{2,}".toRegex(), ".")
   println(answer) // .!@BaT#*.y.abcdefghijklm
```

### 문자열의 처음이나 끝에 있는 단어 제거하기
^은 문자열 시작을 나타내고 $은 문자열 종료를 나타낸다.</br>
|은 or로 a|b라고 하면 a 또는 b와 일치하는 것을 찾는다.

```kotlin
   var answer = "...!@BaT#*..y.abcdefghijklm."	
   answer = answer.replace("^[.]|[.]$".toRegex(), "")
   println(answer) // ..!@BaT#*..y.abcdefghijklm
```


<br/><br/>

---
## 아스키 코드

### 알파벳
65~90 까지가 A에서 Z까지 이고</br>
97~122 까지가 a에서 z까지 이다.

## 기타

### n진수 변환
10진수를 다른 n진수로 변환하고 싶을때는 toString(n)에서 n에 원하는 값을 넣어주면 된다.</br>
원래대로 돌리고 싶을때는 toInt(n)을 사용하면 된다.

```kotlin
	var a = 45
    println(a.toString(8)) // 55
    println(a.toString(8).toInt(8)) // 45
```


<br/><br/>

---
## 확장 함수 / 범위 지정 함수

### let{}
let은 자기 자신을 받아서 결과값을 반환한다.

```kotlin
	val a = 3
    println( a.let{ if(it>3) 3 else 1}) // 1
```

### also{}
also는 let과 비슷해 보일 수 있지만 let은 블록 안의 코드 수행 결과와 상관없이 객체 this를 반환한다.

```kotlin
    var strings = arrayOf("b", "c", "a")
    var newStrings = strings.also{it}
    println(Arrays.toString(strings.also{it.sortBy{it[0]}})) // [a, b, c]
    println(Arrays.toString(newStrings)) // [b, c, a]

```

## 기타

### Character.getNumericValue()
문자열로 된 1 등의 자연수를 toInt()로 변경할 때 아스키 코드 값 때문에 원하는 값을 얻을 수 없다. 이럴 때 Character.getNumericValue()를 사용하면 정수형으로 변경할 수 있다.

```kotlin
	var num = '1'
    println(num.toInt()) // 49
    println(Character.getNumericValue(num)) // 1
```

### maxOf(), minOf()
인수로 입력된 값 중 maxOf()는 가장 큰 값을, minOf()는 가장 작은 값을 반환한다.

```kotlin
    println("max:${maxOf(1,2,3,4)} min:${minOf(1,2,3,4)}") // max:4 min:1
```

### coerceAtMost()
값을 비교하여 더 작은 값을 반환한다.

```kotlin
    var k = 5
    println(k.coerceAtMost(6)) // 5
    println(k.coerceAtMost(2)) // 2
```