# 05 함수 심화학습


### 07 new Function 문법
- `new Function ([arg1, arg2, ...argN], functionBody)` 문법으로도 함수를 만들 수 있습니다.
- 런타임에 받은 문자열을 사용해 함수를 만듭니다.
- 이렇게 만든 함수의 `[[Environment]]` 프로퍼티는 전역 렉시컬 환경을 참조합니다.
  압축기(minifier) 때문에 생길 수 있는 문제를 예방하기 위해서입니다.

### 08 setTimeout과 setInterval을 이용한 호출 스케줄링
