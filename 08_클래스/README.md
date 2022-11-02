### 05 내장 클래스 확장하기

- 내장 클래스를 확장한 클래스의 인스턴스에서 `filter` 등 내장 메서드를 사용하면, 
  객체의 `constructor`를 사용하여 상속받은 클래스의 인스턴스(객체)를 반환합니다.
- 이 동작 방식을 바꾸고 싶다면 특수 정적 getter인 `Symbol.species`를 클래스에 추가하여 사용할 생성자를 반환합니다.
- 내장 객체 간의 상속시 정적 메서드는 상속받지 못합니다.

### 06 'instanceof'로 클래스 확인하기

- `obj instanceof Class`는 `obj`가 `Class`에 속하거나 `Class`를 상속받는지 확인합니다.
  클래스에 정적 메서드 `Symbol.hasInstance`가 구현되어있으면, `Class[Symbol.hasInstance](obj)`가 호출되고,
  아니라면 일반적인 로직으로 `Class.prototype`이 `obj` 프로토타입 체인 중 하나와 일치하는지 확인합니다.
- 비슷한 메서드로 `objA.isPrototypeOf(objB)`도 있지만, Class 생성자를 제외하고 검사한다는 특징이 있습니다.
- `Object.prototype.toString`을 사용해 타입 확인을 넘어 타입을 문자열 형태로 받을 수도 있습니다.

### 07 믹스인

- 단일상속만을 허용하는 자바스크립트에서, 믹스인은 상속받지 않고도 메서드를 사용할 수 있게 해줍니다.
- 메서드 여러 개가 담긴 믹스인 객체를 하나 만들어 `Object.assign(클래스.prototype, 믹스인)`으로 복사합니다.
- 믹스인 안에서 믹스인 상속 가능
- 이벤트 믹스인
