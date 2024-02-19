# 팩토리 패턴 

## 팩토리 패턴

- `객체를 생성하는 코드`를, 호출하는 쪽 (클라이언트)와 분리하여 의존성을 낮추기 위해 사용 
- 객체 필드 등에 수정이 일어나더라도 `객체를 생성하는 코드` 만 수정하면 됨
- 확장에 대해서는 열려고있고 변화에 대해서는 닫혀있어야 한다는 객체지향 원칙을 만족한다.

## 팩토리 패턴의 활용

- 특정 고정 된 값을 클라이언트로부터 감추어서, 클라이언트가 다루어야할 정보의 범위를 줄여주는데 활용할 수 있다.
- 객체 생성시에는 감추고 싶은 값

### AS-IS

외부 API 를 호출하기 위한 RequestDTO 가 있다고 해보자.
```kotlin
class SomeHttpClient {
    
    fun call(someHttpRequest: SomeHttpRequest)
    
    data class SomeHttpRequest (
        val a: A,
        val b: B,
        val c: C,
    )
}
```

팩토리 패턴을 적용하기 전, 클라이언트에서는 아래와 같이 호출하였다.

```kotlin
fun clientFunction(dto: DTO) {
    SomeHttpRequest(
        a = dto.a,
        b = dto.b,
        c = "FIXED_STRING"
    ).run(someHttpClient.call(this))
}
```

### TO-BE
- 팩토리 패턴을 활용하여, 클라이언트가 줄 수 없는 고정된 값을 감출 수 있다.

```kotlin

class SomeHttpClient {

    fun call(someHttpRequest: SomeHttpRequest)
    
    data class SomeHttpRequest (
        val a: A,
        val b: B,
        val c: C,
    ) {
        companion object {
            fun of(_a: A, _b: B) = SomeHttpRequest(
                a = _a,
                b = _b,
                c = "FIXED_STRING"
            )
        }
    }
}
```

### 그냥 c 를 private 으로 만들면 안되나?
- c를 private 으로 선언하면 직접 객체를 생성하는 경우에는 c 라는 필드가 있다는 사실이 클라이언트에 숨겨지게 됨.
- 중요하지 않은 값들을 감춤과 동시에 'c' 라는 필드가 있다는 정보는 드러낼 수 있다.


