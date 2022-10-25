# 07 프로토타입과 프로토타입 상속
### 01 프로토타입 상속
- 객체는 숨김 프로퍼티 `[[Prototype]]`로 `null`이나 다른 객체를 참조합니다. 이 참조 대상을 '프로토타입'이라 부릅니다.
- 객체에 프로퍼티가 없으면 프로토타입에서 찾습니다. 이를 '프로토타입 상속'이라 합니다.
- `__proto__`는 `[[Prototype]]`용 getter/setter입니다. 최근엔 대신 `Object.getPrototypeOf`나 `Object.setPrototypeOf`을 사용합니다.
- 객체엔 오직 하나의 `[[Prototype]]`만 있을 수 있지만, 프로토타입 체이닝은 가능합니다.
- `for..in`은 상속 프로퍼티도 순회합니다. (단, `Object.prototype` 메소드는 제외)

### 02 함수의 prototype 프로퍼티
- new와 생성자 함수로 만든 객체는 생성자 함수의 prototype 프로퍼티가 객체인 경우, 이 정보를 사용해 객체의 `[[Prototype]]`을 설정합니다.
- 모든 함수는 디폴트로 prototype을 갖고, 
  prototype은 constructor 프로퍼티 하나를 가지는 객체를 가리키는데,
  이 constructor 는 함수 자신을 가리킵니다.
- constructor 프로퍼티를 사용해 기존 객체의 constructor로 새로운 객체를 만들 수 있습니다.
  단, 자바스크립트는 올바른 constructor 값을 보장하지 않습니다.
- 모든 함수는 기본적으로 `F.prototype = { constructor : F }`를 가지고 있으므로 "constructor" 프로퍼티를 사용하면 객체의 생성자를 얻을 수 있습니다.

### 03 내장 객체의 프로토타입
- 모든 내장 객체는 프로토타입에 메서드를 저장하고, 객체 자체엔 데이터만 저장합니다.
- 모든 내장 프로토타입의 상속 트리 꼭대기엔 `Object.prototype`이 있습니다.
- 프로토타입 체인 중 중복 메서드가 있다면 가장 가까운 곳에서 가져옵니다.
- 원시값(단, `null` `undefined` 제외)의 프로퍼티에 접근하려 하면 임새 래퍼 객체가 생성됩니다.
- 네이티브 프로토타입은 수정할 수 있습니다. 하지만 폴리필을 제외하면 추천하지 않습니다.
- 네이티브 프로토타입에서 메서드를 빌려올 수 있습니다.

### 04 프로토타입 메서드와 __proto__가 없는 객체
- `__proto__`는 브라우저 환경에선 구식입니다. 모던한 방식으로는:
  - `Object.create(proto, [descriptors])` <- 객체 복제에도 효과적입니다.
  - `Object.getPrototypeOf(obj)`
  - `Object.setPrototypeOf(obj, proto)`
- `__proto__`를 키로 사용하려할 때 할당이 되지 않거나 프로토타입을 바꾸는 치명적인 버그를 발생시킬 수 있습니다.
  객체 대신 맵을 사용하거나, `Object.create(null)`로 프로토타입이 없는 "아주 단순한" 혹은 "순수 사전식" 객체를 사용해 예방할 수 있습니다.
  
