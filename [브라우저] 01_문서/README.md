### 06 속성과 프로퍼티
- HTML의 속성과 DOM 객체의 프로퍼티
- DOM 노드는 일반 객체이므로 표준이 아닌 프로퍼티나 메서드를 추가할 수 있습니다.
- 브라우저는 HTML을 파싱해 DOM 객체를 만들 때, 표준 속성을 인식해 DOM 프로퍼티를 만듭니다.<br>
  하지만 비표준 속성인 경우, 이에 매핑하는 DOM 프로퍼티가 생성되지 않습니다.
- 비표준 속성은 `hasAttribute` `getAttribute` `setAttribute` `removeAttribute` `attributes`로 접근할 수 있습니다.
- 표준 속성이 변하면 대응하는 프로퍼티는 자동으로 갱신됩니다.<br>
  마찬가지로, 프로퍼티가 변하면 대응하는 속성도 갱신됩니다. (단, `input.value` 등 몇몇은 속성->프로퍼티로만 동기화됩니다)
- 비표준 커스텀 속성을 사용하는 것이 클래스를 사용하는 것보다 선호되는 경우도 있습니다.
- 비표준 속성을 사용하는 또다른 방법으로 `dataset`이 있습니다.
- (정확한 HTML 속성 값이 필요한 몇몇 경우를 제외하고) 거의 모든 상황에서 속성보다는 프로퍼티를 사용하는 게 낫습니다.

### 07 문서 수정하기
- 요소/문자 노드 삽입시 대부분은 `append/prepend/before/after`을 사용하고, 그 외엔 주로 `insertAdjacentHTML`을 사용합니다.
- 노드 생성
  - `.createElement(tag)`
  - `.createTextNode(value)`
- 노드 복제
  - `.cloneNode(deep)`
- 노드 삽입, 삭제
  - `append` / `prepend` / `before` / `after` : 문자열을 넘기면 'HTML'이 아닌 '문자열' 자체로 삽입됩니다.
  - `replaceWith`
  - `.insertAdjacentHTML(where, html)` : HTML이 이스케이프 처리되지 않고 그대로 삽입됩니다.
- 노드 삭제
  - `remove`
- `DocumentFragment`
- `document.write`
