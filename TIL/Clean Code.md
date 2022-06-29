# CleanCode

> 캠프장은 처음 왔을 때보다 더 깨끗하게 해 놓고 떠나라.
> 

## 네이밍

- 의도를 분명히 밝혀라
    - 이름이 존재하는 이유, 수행하는 기능, 사용 방법을 나타내야 한다.
- 이름으로 혼란주지 마라
    - 사용화된 단어를 다른 이유로 사용하지 말자
    - 흡사한 이름또한 피하는것이 좋다.
- **변수 이름에 타입을 넣지 않는다**
- 클래스 이름은 명사나 명사구가 좋다
- 메서드 이름은 동사나 동사구가 좋다
    - 표준에 따라 `get`, `set`, `is`를 사용한다.
    - 생성자를 중복 정의할 때에는 정적 팩토리 메서드를 사용하는 것이 좋다.
- 기발한 이름은 피해라 ex) (emd→읍면동)?
- 일관성 있는 어휘를 사용하자
- 검색하기 쉬운 단어를 사용하기
    - 긴 단어 > 짧은 단어
    - 검색하기 쉬운 이름 > 상수
    - 이름 길이는 사용되는 범위에 비례한다.

### 함수

- 함수는 작을수록 좋고, 들여쓰기는 적을수록 좋다.
- 한가지 기능만 있어도 충분하다
- 함수 당 추상화 수준은 동일하게 하기
    - 코드는 위에서 아래로 읽혀야 한다.
- 서술적인 이름을 사용하자
- 함수 인수는 적을수록 좋다.
    - 가장 좋은 경우는 인수가 없는 것, 다음에는 단항 함수(인수가 1개)이다.
    - 입력값이 있는 변환 함수는 반환 값이 있는 것이 좋다.
    - 플래그 인수(ex. isTrue)는 사용하지 않는 것이 좋다.
    - 인수가 많이 필요하다면 독자적인 클래스 생성을 고려해보는 것도 좋은 방법이다.
- 중복을 제거하자
- 명령과 조회 분리하기
    - 함수는 무언가를 수행하거나 답하거나 둘 중 하나만 해야 한다.

### 주석

> 복잡하고 어수선하며 주석이 많이 달린 코드를 만드는 것보단 표현력이 풍부하고 깔끔한 코드를 만드는데 집중해야 한다.
> 
- 주석은 가능한 적은 게 좋다
- 코드로 표현하지 못하는 정보를 제공해야 한다.
- 의도를 설명하는 주석
- 결과를 경고하는 주석
- 중요성을 강조하는 주석
- 주석으로 처리한 임시 코드는 정리하자
- 이력을 기록하는 주석은 필요 없다
- 코드로 설명할 수 있는데, 코드를 설명하는 주석은 지우자

### ****형식****

- 개념은 빈 행으로 분리하라
- 밀접한 개념은 서로 까까이 두자
- 호출하는 함수를 먼저 당하는 함수를 가까이 배치하자

### 객체와 자료구조

- 자료를 추상화 하자
    - 아무생각없이 조회, 설정 함수를 추가하는것보다 자료를 표현하기 위한 최상의 방법 탐구
- 객체 지향과 절차 지향을 상황에 맞게 선택하라
- **디미터 법칙**을 위반하지 마라
    - 모듈은 자신이 조작하는 객체의 속사정을 몰라야 한다.

### 오류 처리

<aside>
⚠️ 예외란 프로그램 내에서 발생하여 프로그램 내에서 처리가 가능한 것
</aside>
<br />
<aside>
⚠️ JVM 내에서 발생하는 에러로 프로그램 내에서 처리가 불가능 한 것
</aside>

![예외](https://user-images.githubusercontent.com/101608868/176375615-5ccd1b0b-8991-4160-b781-6ea2fea1508e.png)

**[ 확인된 예외(checked exception) ]**

- 잘못된 코드가 아닌 잘못된 상황에서 발생하는 예외
- 파일 열기와 같이 정확한 코드로 구현했음에도, 외부 환경에 따라 발생 가능
- 예외처리를 구현하지 않으면 컴파일 에러 발생 (컴파일 시 확인해서 확인된 예외)
- RuntimeException 이외의 예외들

**[ 미확인 예외(unchecked exception) ]**

- 런타임 시 잘못 구현된 코드로 인해 발생하는 예외
- 컴파일 에러가 나지 않지만 적절한 예외처리가 없을 경우 프로그램이 강제 종료
- 컴파일 시 확인하지 않기 때문에 미확인 예외
- RuntimeException에 포함된 예외들

- 미확인 예외를 사용하자
    - 확인된 예외는 상위 선언부에서 모두 선언해주어야 하기 때문이다 → OCP 위반
- 예외에 의미를 제공하자
- 호출자를 고려해 예외 클래스를 정의하라
    - 외부 라이브러리를 사용할 때에는 라이브러리용 클래스를 고려해보는 것이 좋다.
- null을 반환하지 마라

## 단위 테스트

- TDD법칙
    - 실패하는 단위 테스트를 작성할 때까지 실제 코드를 작성하지 않는다
    - 컴파일은 실패하지 않으면서 실행이 실패하는 정도로만 다위 테스트를 작성한다.
    - 현재 실패하는 테스트를 토오가할 정도로만 실제 코드를 작성한다.
- 테스트는 유연성, 유지보수성, 재사용성을 제공한다
- 테스트는 실제 코드보다 더 가독성이 중요하다.
- 테스트 당 개념 하나
    - 테스트의 assert를 최소로 하라
    - 테스트 함수 하나는 개념 하나만 테스트하라
- **F.I.R.S.T**
    - **F**ast : 테스트는 빨리 돌아가야 한다.
    - **I**ndependent : 테스트는 서로 의존하면 안 된다. 한 테스트가 다음 테스트의 실행을 준비해서도 안 된다.
    - **R**epeatable : 테스트는 어떤 환경에서도 반복 가능해야 한다. ( 네트워크가 없어도 실행 )
    - **S**elf-Validating : 결괏값은 boolean 이여야 한다. (성공/실패)
    - **T**imely : 실제 코드 구현 전에 작성해야 한다.

## **동시성**

Computer Science 에서 Concurrency(동시성)은 프로그램, 알고리즘 또는 문제가 실행되는 부분에서 최종 결과에 영향을 주지 않는 단위의 기능이다. 이를 통해 병렬실행이 가능하여 다중 프로세서 및 다중코어 시스템에서 전체 실행 속도를 크게 향상 시킬 수 있다.

정말 정말 너무 어렵다. 중요한건 알겠는데 정말 어렵다 ㅜㅜ 

동시성을 사용하면 **무엇(what)** 과 **언제(when)** 를 분리할 수 있다.

### 동시성 방어 원칙

- 공유 객체 하나에는 메서드 하나만 사용하는 것이 좋다.
- 다중 스레드 코드는 버그를 찾기 어렵기 때문에 각별히 깨끗하게 코드를 짜야한다.
- **SRP**를 준수하는 게 좋다.
- POJO를 사용해 스레드를 아는 코드, 모르는 코드를 **분리하는 게** 좋다.
- 스레드 코드를 테스트할 때에는 전적으로 **스레드만 테스트**한다.
- 동시성 오류를 일으키는 **잠정적 원인**을 철저히 이해한다.
- **사용하는 라이브러리**와 **기본 알고리즘**을 이해한다.
- 보호할 코드 영역을 찾아내는 방법과 특정 코드 영역을 잠그는 방법을 이해한다.
- 어떻게든 문제가 생기기 때문에 **테스트**는 정말 중요하다.

## 좋은 코드란 무엇인가? [느낀점]

이 책을 읽은 이유는 내가 깨끗하고 좋은 코드를 작성할 수 있도록 조언을 구하기 위해서다. 
결론적으로 좋은 코드란 엄청난 가독성과 유지보수성을 가진 코드인것 같다.
코드를 처음 보는 사람도 쉽게 읽을 수 있고, 원하는 기능을 바로바로 찾는것또한 중요하다.
미래에 내 후임이 이 코드를 보더라도 나를 욕하지 않도록 코드를 예쁘게 짜야한다고 생각한다.