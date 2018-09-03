# DI (Dependency Injection)

## DI의 이점

위키피디아 왈:
의존 관계 설정이 컴파일시가 아닌 실행시에 이루어져 모듈들간의 결합도 를 낮출 수 있다.
코드 재사용을 높여서 작성된 모듈을 여러 곳에서 소스코드의 수정 없이 사용할 수 있다.
모의 객체 등을 이용한 단위 테스트의 편의성을 높여준다.

## @Inject

디펜던시 요청. 이 어노테이션을 달면 대거가 인스턴스를 만들어서 집어넣어줌

## @Module

이 어노테이션이 붙여진 클래스는 디펜던시를 다른 클래스들에게 주입하는 역할을 함.
중요한 기능 중 하나는 이 모듈이 나눠지거나 서로 합쳐질 수 있다는 것.

## @Provide

@Module로 지정한 클래스의 메소드에 다는 어노테이션.
이 어노테이션을 통해서 어떻게 의존성을 만들고 주입할지 명시

## @Component

흠.. 잘 이해가 안가는데?
Inject를 받는 인스턴스와 @Module 사이의 다리 역할이라고 하는데..
컴포넌트에 있는 모듈을 보면 그 컴포넌트가 어떤 디펜던시를 제공하는지 알 수 있다.
이건 이해가 됨.

## @Scope

객체의 생명 주기를 정의하는 어노테이션.
예를 들어 @PerActivity라면 액티비티가 살아있는 동안 존재하는 객체라는 걸 알 수 있음.
사용자가 직접 커스텀할 수 있다고 함.


<!-- Talk from Jake Wharton -->

## Module

Create a Factory instance for each methods.

In Factory, the module is injected and
call the associated method of the module.

If any parameter is needed, the provider of that parameter is also injected.


## Component

create a Builder - set `modules` which are listed above the class definition. + also `dependencies` too.

Implement Component prefixed with 'Dagger'.
It receives the Builder of it.

Create providers for the defined module, using Factory classes generated with `@Module` annotation.
Wrap the providers with ScopeProvider for giving them corresponding scopes.

Implement exposed dependencies (methods declared in the Component interface) using proviers above.

If a class have fields annotated with '@Inject', then create providers for the fields and
bind them when the Factory creates an instance.

