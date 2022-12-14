# 05 함수 심화학습
### 01 재귀와 스택
- 재귀(recursion) – 함수 내부에서 자기 자신을 호출하는 것을 나타내는 프로그래밍 용어
- 재귀 깊이는 스택에 들어가는 실행 컨텍스트 수의 최댓값
- 재귀를 이용해 작성한 코드는 반복문을 사용한 코드로 다시 작성 가능
  - 재귀를 반복문으로 바꾸는 것이 대게 메모리를 적게 사용하지만, 큰 개선이 없는 케이스도 몇 있음. 
  - 재귀를 사용하면 코드가 짧아지고 코드 이해도가 높아지며 유지보수에도 이점이 있음

### 02 나머지 매개변수와 스프레드 문법
- 상당수의 자바스크립트 내장 함수는 인수의 개수에 제약을 두지 않습니다.
  또한, 함수 정의와 상관 없이 함수에 넘겨주는 인수의 개수엔 제약이 없습니다.
- `"..."`은 나머지 매개변수나 스프레드 문법으로 사용할 수 있습니다.
  - 나머지 매개변수: `...`이 함수 매개변수의 끝에 있으면 인수 목록의 나머지를 배열로 모아줌. 인수 개수에 제한이 없는 함수를 만들 때 사용
  - 스프레드 문법: `...`이 함수 호출 시 사용되거나 기타 경우엔 배열 -> 인수 목록으로 확장. 다수의 인수를 받는 함수에 배열을 전달할 때 사용
- 조금 오래된 방법이긴 하지만 `arguments`라는 반복 가능한(이터러블) 유사 배열 객체를 사용해도 인수 모두를 사용할 수 있습니다.

### 03 변수의 유효범위와 클로저
- 실행 중인 함수, 코드 블록, 스크립트 전체는 **렉시컬 환경**이라 불리는 내부 숨김 연관 객체를 갖습니다.
- 렉시컬 환경 객체는 환경 레코드, 외부 렉시컬 환경으로 구성됩니다.
- 스크립트가 시작되면 스크립트 내에서 선언한 변수 전체가 uninitialized 상태로 렉시컬 환경에 pre-populated됩니다.
  let을 만나면 변수를 사용할 수 있으며, 초기화 전까지 값은 `undefined`입니다.
- 함수 선언문은 함수 표현식이나 일반 변수와 달리 바로 초기화됩니다.
- 함수를 호출해 실행하면 새로운 렉시컬 환경이 만들어집니다.
  함수는 `[[Environment]]`라는 숨김 프로퍼티에 함수가 만들어진 곳의 렉시컬 환경에 대한 참조를 저장합니다.
- 코드에서 변수에 접근할 땐, 먼저 내부 렉시컬 환경을 검색 범위로 잡습니다. 내부 렉시컬 환경에서 원하는 변수를 찾지 못하면 검색 범위를 내부 렉시컬 환경이 참조하는 외부 렉시컬 환경으로 확장합니다. 이 과정은 검색 범위가 전역 렉시컬 환경으로 확장될 때까지 반복됩니다.
- '클로저'는 외부 변수를 기억하고 접근할 수 있는 자바스크립트 함수입니다.
- 외부 변수는 자바스크립트 엔진이 계속해서 최적화합니다. (자바스크립트 엔진은 변수 사용을 분석하고 외부 변수가 사용되지 않는다고 판단되면 이를 메모리에서 제거합니다.)

### 04 오래된 var
- `var`는 함수 스코프이거나 전역 스코프입니다.
- `var`의 선언은 함수 최상위로 호이스팅되지만, 할당은 호이스팅되지 않습니다. 
  - `var` 선언은 함수가 시작되는 시점(전역 공간에선 스크립트가 시작되는 시점)에서 처리됨
- `var`만 있었을 때 블록 레벨 스코프를 사용하기 위해 즉시 실행 함수 표현식(IIFE)을 사용했습니다.
  - 함수 표현식을 괄호로 둘러쌓으면 `(function {…})` 함수 표현식이 만들어지고 바로 호출되면서, 해당 함수가 바로 실행됨

### 05 전역 객체
- 전역 객체를 사용하면 어디서나 사용 가능한 변수나 함수를 만들 수 있습니다. 
- 전역 객체는 언어 자체나 호스트 환경에 기본 내장되어 있는 경우가 많습니다.
  호스트 환경마다 부르는 이름이 다른데, 최근 `globalThis`로 표준화하는 추세입니다.
- 모듈을 사용하고 있지 않다면, var로 선언한 전역 함수/변수는 전역 객체의 프로퍼티가 되지만, 이런 사용은 지양합니다.
  중요한 변수를 전역으로 사용하려면 전역 객체에 직접 추가합니다. (예: `window.x`)
  프로젝트 전체에서 꼭 필요한 변수만 전역 객체에 저장하도록 하고, 전역 변수는 가능한 한 최소한으로 사용합시다.
- 전역 객체로 브라우저가 자바스크립트 기능을 지원하는 지 확인한 후, 직접 구현해 폴리필할 수 있습니다.

### 06 객체로서의 함수와 기명 함수 표현식
- 함수는 객체입니다. 
- 객체로서의 함수에 사용할 수 있는 프로퍼티로는 `name` 과 `length`(매개변수의 개수) 가 있습니다.
  - 인수의 종류에 따라(여기선 인수의 `length` 프로퍼티 값에 따라) 인수를 다르게 처리하는 방식을 **다형성(polymorphism)** 이라 합니다. 
- 커스텀 프로퍼티를 만들 수도 있습니다. 이는 클로저를 대체할 수도 있지만, 함수 외부에서도 값을 수정할 수 있다는 단점이 있습니다.
- 기명 함수 표현식을 사용해 중첩 함수에서 이름으로 자기 자신을 참조할 수 있습니다. 
  외부 코드에 의해 함수가 변경되는 문제를 막을 수 있습니다.

### 07 new Function 문법
- `new Function ([arg1, arg2, ...argN], functionBody)` 문법으로도 함수를 만들 수 있습니다.
- 런타임에 받은 문자열을 사용해 함수를 만듭니다.
- 이렇게 만든 함수의 `[[Environment]]` 프로퍼티는 전역 렉시컬 환경을 참조합니다.
  압축기(minifier) 때문에 생길 수 있는 문제를 예방하기 위해서입니다.

### 08 setTimeout과 setInterval을 이용한 호출 스케줄링
- `setTimeout`으로 일정 시간이 지난 후에 함수를 실행할 수 있습니다.  
  `clearTimeout(타이머 식별자)`로 취소할 수 있습니다.
- `setInterval`로 시간 간격을 두고 함수를 실행할 수 있습니다.  
  `clearInterval(타이머 식별자)`로 중단할 수 있습니다.
- 중첩 `setTimeout`으로도 일정 간격을 두고 실행할 수 있습니다.
  더 유연하고, (대개) 지연 간격을 보장한다는 장점이 있다.
- 둘에게 넘긴 함수는 완료시까지 가비지 컬렉션의 대상이 되지 않기 때문에, 스케줄링할 필요가 없어진 함수는 아무리 작더라도 취소하도록 합니다.
- 브라우저 환경에서 실제 대기 시간은 0이 아닙니다.

### 09 call, apply와 데코레이터, 포워딩
- 인수로 받은 함수를 감싸 기능을 추가하는 함수를 데코레이터라고 합니다.
- 이를 객체 메서드에 사용하려면 `f.call()`로 `this`를 고정해주어야 합니다.
- 좀 더 빠른 `f.apply()`를 사용할 수도 있습니다.
  이처럼 컨텍스트와 함께 인수 전체를 다른 함수에 전달하는 것을 콜 포워딩이라고 합니다.
- 메서드 빌리기
- 함수에 프로퍼티가 있는 경우엔 데코레이터 사용에 주의해야 합니다. 이후 배울 `Proxy`가 필요합니다.

### 10 함수 바인딩
- 객체 메서드가 객체 내부가 아닌 다른 곳에 전달되어 호출될 때 `this` 정보가 사라지는 문제가 있습니다.
- 해결 방법 1) 래퍼 함수를 사용합니다. 취약점이 있습니다.
- 해결 방법 2) `bind`를 사용해 컨텍스트를 바인딩합니다.
- `this`뿐만 아니라 인수도 바인딩 가능합니다. 인수 일부를 고정한 함수를 부분 적용 함수라 부릅니다.

### 11 화살표 함수 다시 살펴보기
- 화살표 함수는 컨텍스트가 있는 긴 코드보다는 자체 '컨텍스트’가 없는 짧은 코드를 담을 용도로 만들어졌습니다.
- `this`를 가지지 않습니다.
- `arguments`를 지원하지 않습니다.
- `new`와 함께 호출할 수 없습니다.
- 이 외에도 `super`가 없다는 특징도 있는데, 이번 챕터에선 다루지 않았습니다.
