# 02_코드_품질 (요약)

### 01 Chrome으로 디버깅하기
### 02 코딩 스타일
- 요즘엔 이미 작성된 스타일 가이드(예: Airbnb의 자바스크립트 스타일 가이드) 중 하나를 선택해 팀의 가이드로 삼는 편입니다.
- Linter(예: ESLint)라는 도구로 코드가 스타일 가이드를 준수하고 있는지를 자동으로 확인할 수 있습니다.
- 추천할만한 규칙   
![image](https://user-images.githubusercontent.com/65887537/193510428-c347f49f-9651-45fb-93b7-a658b95d924f.png)


### 03 주석
- 주석에는 고차원 수준 아키텍처, 함수 용례, 직관적이지 않은 해결 방법에 대한 설명이 들어가면 좋습니다.
- 코드의 동작방법에 대한 설명 등, 코드를 읽어서 알 수 있는 내용은 들어가지 않는 게 좋습니다.

### 04 닌자 코드
- Behavior Driven Development(BDD)는 test, documentation, example 을 모아놓은 개념입니다.
- 코드를 작성하기 전 코드가 할 일을 자연어로 표현한 것을 BDD에선 명세서 또는 스펙이라 부릅니다.  
  스펙은 세 가지 구성요소(`describe`, `it`, `assert.*`)로 이루어집니다.
- 하나의 테스트(`it`)에선 한 가지만 확인합니다. `for`문이나 중첩 `describe`를 사용할 수 있습니다.
- `before/after`와 `beforeEach/afterEach`

### 05 테스트 자동화와 Mocha
- Behavior Driven Development(BDD)는 test, documentation, example을 한데 모아놓은 개념입니다.
- 명세서 혹은 스펙은 `describe` `it` `assert.*`로 구성됩니다.
- 테스트(`it`) 하나에선 한 가지만 확인하도록 합니다.
- `before/after`와 `beforeEach/afterEach`

### 06 폴리필
- 바벨은 모던 자바스크립트 코드를 구 표준을 준수하는 코드로 바꿔주는 트랜스파일러 입니다.
- 기존 코드가 구 표준을 준수하는 코드로 변경하는 트랜스파일러와 추가된 내장 함수 표준을 준수할 수 있게 함수를 구현하거나 수정하는 폴리필 역할을 합니다.
