---

## title: "[Swift] Closure를 활용해 간단한 계산하기" 
subtitle: Closure add, sub, mul, div
tags: Swift, Ios, Closure
published: true

---

# 정수의 합을 구하는 Closure

```swift
var addClosure: (Int, Int) -> Int = { 
(a: Int, b: Int) -> Int in return a + b }
```

위 코드는 간소화 하지않은 가장 기본적인 형태의 `closure` 로 두 개의 정수를 `parameter` 로 받아 합을 반환하는 `closure` 입니다.

코드를 봤을때 조금 복잡해보이지만 `closure` 는 코드를 간략화 할 수 있는 강력한 기능을 가지고 있습니다. 
<br>
<br>
<br>
## Closure 간소화하기

### 타입 생략

먼저 앞에서 `parameter` 가 `Int` 라고 선언 되었으니 `closure` 는 타입 추론을 통해 a 와 b 가 자연스럽게 `Int` 라는 것을 알 수 있습니다.  이를 줄여보면

```swift
var addClosure: (Int, Int) -> Int = { 
(a, b) -> Int in return a + b }
```

이처럼 a 와 b의 타입이 `Int` 라고 명시하지 않고 줄일 수 있습니다.
<br>
<br>
<br>
### 반환 타입 생략

위에서 타입을 생략한 것처럼 반환 타입 또한 `Int` 라고 앞에서 선언해두었기 때문에 생략이 가능합니다. 줄여보면 아래 코드처럼 되겠네요

```swift
var addClosure: (Int, Int) -> Int = { 
(a, b) in return a + b }
```

원래는 (Int, Int) → Int 이 형태를 갖춰주기 위해 소괄호 `()` 가 존재했는데 반환 타입을 생략했기 때문에 같이 생략해줍니다.

```swift
var addClosure: (Int, Int) -> Int = { 
a, b in return a + b }
```

점점 짧아지고 있네요 !
<br>
<br>
<br>
### 파라미터를 인덱스로 표현하기

```swift
var addClosure: (Int, Int) -> Int = { $0 + $1 }
```

위 코드는 조금 당황스러울 수도 있는데요 쉽게 생각하면 `$0` 은 첫번째 파라미터를 가르키고 `$1` 은 두번째 파라미터를 가르킵니다. 이렇게 사용할땐 `a, b in return` 이 부분이 모두 생략이 가능합니다.
<br>
<br>
<br>
### 너무 줄이지 않기!

지금은 간단한 코드라 쉽게 읽히지만 코드의 로직이 복잡해질 수록 너무 간략화 된 `closure` 는 이해하는데 어려울 수 있습니다ㅜㅜ 

> 우리는 항상 **가독성**을 중요하게 생각해야 합니다.

그래서 제가 생각했을 때는 이정도까지만 줄이는 게 좋은 것 같습니다 !

이는 ~~개인적인 견해입니다.~~

```swift
var addClosure: (Int, Int) -> Int = { a, b in return a + b }
```
<br>
<br>
<br>
# 정수의 뺄셈을 구하는 Closure

위에서 `closure` 를 간략화 하는 방법을 배웠으니 바로 축약해서 작성해보겠습니다.

```swift
var subClosure: (Int, Int) -> Int = { a, b in return a - b }
```
<br>
<br>
<br>
# 정수의 곱셈을 구하는 Closure

```swift
var mulClosure: (Int, Int) -> Int = { a, b in return a * b }
```
<br>
<br>
<br>
# 정수의 나눗셈을 구하는 Closure

```swift
var divClosure: (Int, Int) -> Int = { a, b in return a / b }
```
<br>
<br>
<br>
# Closure를 활용한 계산

## 함수 선언

위에서 계산을 해줄 `closure` 들을 만들었으니, 활용해보기 위해 `parameter` 로 두 개의 정수와  앞에서 만든 `closure` 를 입력받아 계산을 할 수 있도록 만들어 보았습니다.

```swift
func calculateTwoNum(a: Int, b: Int, operation: (Int, Int) -> Int) -> Int {
    let result = operation(a, b)
    return result
}
```
<br>
<br>
<br>
## 함수 호출

이는 다음과 같이 호출이 가능합니다.

```swift
calculateTwoNum(a: 5, b: 4, operation: addClosure)
calculateTwoNum(a: 4, b: 2, operation: subClosure)
calculateTwoNum(a: 5, b: 6, operation: mulClosure)
calculateTwoNum(a: 3, b: 2, operation: divClosure)
```
<br>
<br>
<br>
## 전체 코드 및 호출 결과
![image](https://user-images.githubusercontent.com/60254939/126871986-7cf64313-cc0e-41d0-a863-fc68288c768d.png){:.border.rounded.shadow}

