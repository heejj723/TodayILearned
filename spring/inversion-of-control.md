# 의존성 주입과 제어의 역전



## 의존성 주입 (Dependency Injection)
Spring에서의 의존성 주입이란 다음과 같다.

어떤 객체에 스프링 컨테이너가 또 다른 객체와 의존성을 맺어주는 행위

## 제어의 역전 (Inversion of Control)
제어의 역전은 의존성 주입의 상위 개념으로, 다음과 같다.

> 스프링 컨테이너가 필요에 따라 개발자 대신 Bean들을 관리(제어)해주는 행위

일반적인 상황에서는 개발자가 직접 객체를 제어해야 했다. new 연산자를 통해 객체를 생성하고, 객체의 의존성을 맺어주고, 초기화를 해주고 등등...

하지만 Spring 에서는 xml파일 또는 어노테이션 방식으로 스프링 컨테이너에 Bean(객체)를 등록하기만 하면, 스프링 컨테이너에서 Bean의 생명주기(생성 -> 의존성 설정 -> 초기화 -> 소멸)를 전부 관리해준다.

즉, **객체에 대한 제어권**이 컨테이너로 역전되기 때문에 제어의 역전이라고 하는 것이다.

## 장점
개발자는 객체 관리에 덜 신경쓸 수 있게 되어 다른 부분에 더 집중할 수 있게 됨
약한 결합(참고 링크)을 이용하여 객체 간 의존 관계를 쉽게 변경할 수 있음 </br>

결론적으로 코드의 재사용성과 유지보수성을 높인다.

## 정리
Spring에서는 제어의 역전을 지원하여, 필요에 따라 개발자대신 스프링 컨테이너가 객체(Bean)들을 제어해준다.

스프링 컨테이너는 Bean들의 생명주기(생성 -> 의존성 설정 -> 초기화 -> 소멸)을 관리하며, 필요에 따라 객체 간 의존성 주입을 해준다.
제어의 역전은 의존성 주입의 상위 개념이다.

제어의 역전은 코드의 재사용성과 유지보수성을 높인다