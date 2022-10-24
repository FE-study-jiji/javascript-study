# 06 객체 프로퍼티 설정
### 01 프로퍼티 플래그와 설명자
- 객체 프로퍼티는 값과 함께 `writable`, `enumerable`, `configurable`이라는 세 플래그를 갖습니다.
- `Object.getOwnPropertyDescriptor`로 프로퍼티 값과 플래그 정보를 받아볼 수 있고,
  `Object.defineProperty`로 플래그를 변경할 수 있습니다.
- 일반적인 방식으로 프로퍼티를 만들면 모두 true가 되고, 
  `Object.defineProperty`로 만들면 따로 명시하지 않을 시 자동으로 false가 됩니다.
  
### 02 프로퍼티 getter와 setter
- 객체의 프로퍼티는 데이터 프로퍼티와 접근자 프로퍼티로 나뉩니다.  
  둘은 다른 설명자를 가지며, 프로퍼티는 한 종류에만 속할 수 있습니다.  
- 접근자 프로퍼티의 본질은 함수로, get과 set하는 역할을 담당합니다.  
  획득자 메서드와 설정자 메서드는 각각 `get`과 `set`으로 나타냅니다.  
  읽고 쓸 수 있지만 존재하지는 않는 가상의 프로퍼티가 생깁니다.  
