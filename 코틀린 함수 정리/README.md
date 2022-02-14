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

java.util.Arrays을 호출하여 1차원 배열을 출력할 수 있다.

```kotlin
    var arrayOf = arrayOf("Hello", "world")
    println(Arrays.toString(arrayOf)) // [Hello, world]
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


---

## :: (더블 콜론)
변수앞에 ::을 명시하면 변수를 객체로 액세스하여 객체에 대한 속성을 참조하게 된다.</br>

```kotlin
    var array1 = arrayOf(1, 2, 3, 4, 5)
    var array2 = arrayOf(1, 2, 8, 6, 5)
    println(array1.filter(array2::contains)) // [1, 2, 5]
```

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
