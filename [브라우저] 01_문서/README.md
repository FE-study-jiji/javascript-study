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

### 08 스타일과 클래스
- 요소에 스타일을 적용하는 방법
  - CSS 클래스 추가
  - `style` 프로퍼티 수정
- 클래스를 관리할 수 있게 해주는 DOM 프로퍼티:
  - `className` – 클래스 전체를 문자열 형태로 반환해줍니다. 클래스 전체를 바꾸고싶을 때 유용합니다.
  - `classList` – 개별 클래스를 조작할 때 유용합니다. `add/remove/toggle/contains`가 구현된 객체를 반환합니다. 
- 스타일 변경 방법:
  - `style` 프로퍼티 – `style` 속성 값에 대응되는 객체입니다. 
    여러 단어를 이어서 만든 프로퍼티 이름는 카멜 표기법으로 변환합니다. 
    프로퍼티를 제거해야 한다면 빈 문자열을 할당합니다. 전체 스타일을 설정하려면 `style.cssText`를 사용합니다.
  - 클래스로 적용한 스타일값(CSS cascade 값)은 `getComputedStyle(elem)`으로 읽을 수 있습니다.
    계산값이 아닌 결정값을 반환합니다.

### 09 요소 사이즈와 스크롤
- 자바스크립트는 요소의 기하 프로퍼티를 지원합니다.
  - `offsetParent`
  - `offsetLeft` `offsetTop`
  - `offsetWidth` `offsetHeight`
  - `clientLeft` `clientTop`
  - `clientWidth` `clientHeight`
  - `scrollWidth` `scrollHeight`
  - `scrollLeft` `scrollTop`
- 스크롤바를 움직일 수 있게 해주는 scrollLeft와 scrollTop을 제외한 모든 프로퍼티는 읽기 전용입니다.

### 10 브라우저 창 사이즈와 스크롤
- `document.documentElement.clientWidth/clientHeight` : 창(스크롤바 등을 제외한 사용자 눈에 보이는 영역)의 너비와 높이
- 스크롤에 가려진 영역을 포함한 전체 너비와 높이는 6개 값 중 최대값을 구하는 방식을 사용합니다.
- 스크롤 관련
  - `window.pageYOffset` / `pageXOffset`
  - `window.scrollTo(pageX,pageY)` / `window.scrollBy(x,y)`
  - `elem.scrollIntoView(top)`
  - `document.body.style.overflow = "hidden"`

### 11 좌표
- 페이지 내 모든 점은 다음과 같은 좌표를 갖습니다.
- 창 기준 좌표는 `elem.getBoundingClientRect()`로 구할 수 있습니다.  
  해당 함수는 `x`, `y`, `width`, `height` 등의 프로퍼티 및 `top`, `bottom`, `left`, `right` 등의 파생 프로피티를 제공합니다.  
  `position:fixed`와 사용하면 좋습니다.
- 문서 기준 좌표는 창 기준 좌표 + 현재 스크롤 상태 로 구할 수 있습니다.   
  `position:absolute`와 사용하면 좋습니다.
  
