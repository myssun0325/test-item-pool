## 검색자동완성 만들기
먼저 아래 기획서 내용을 참고한다.

- https://docs.google.com/presentation/d/1E0HUKbGFaGpGIyZFbQ5iyX-egynVwXqfGqwl42VE1g4/edit#slide=id.g26ec6ac978_0_0

검색자동완성은 아마존에서 제공하는 검색창에서의 자동완성 텍스트를 만드는 기능이다.

위 기획서를 참고하고, 이해를 돕기 위해 amazon.com에서 자동완성 기능을 직접 체험하는 것이 좋다.

### 1. 기능요구사항
- HTML,CSS를 라이브러리 없이 구현한다.  (less, bootstrap 등 금지)
- 디자인이 너무 이쁘지 않아도 괜찮지만, 일관된 디자인을 적용해야 한다. 특히 UI의 일정하고 규칙적인 배치는 중요하다.
- JAVASCRIPT역시 라이브러리 없이 구현한다. (syntax는 자유, ES5,ES6 모두 가능)
- 브라우저 호환성은 크게 고려하지 않고 최신브라우저를 지원.
- 자동완성 데이터는 AJAX로 응답을 받아서 보여준다. 
- 자동완성 결과화면에서 일치하지 않는 부분만 굵게 보여야 한다.(아마존도 그렇게 동작한다)
- 똑같은 데이터를 요청하면, 서버로 보내지 않고 재사용한다. 하지만 1분이 지난 데이터는 다시 서버로 요청해서 받아온다. 
- '최근검색어' 기능을 개발한다. 검색버튼(돋보기)을 눌렀던 검색어는 기억했다가, 다시 접속시 검색창에 포커스가 갈때 '최근검색어'로 노출되야 한다. 노출방식은 자동완성영역과 같은 위치에서 노출되야 한다. (네이버의 최근검색어 기능을 참고한다)
- 검색창 입력 우측끝에는 'x'버튼이 있어 이것을 누르면 검색어가 삭제되고, 다시 최근검색어가 노출되도록 한다.

### 2.백엔드 구성
- JSON응답을 할 수 있는 nodeJS + express 환경을 갖추고 응답처리한다.(백엔드 구성이 nodejs나, express가 아니여도 괜찮다)
- DB가 없음으로 우리는 특정 문자열(예로 'JAVASCRIPT')을 선택해서, 한글자씩 입력할때마다 자동완성이 되는 기능을 만든다.
- JSON 샘플 데이터는 아마존 사이트에 접속해서, 크롬 개발자 도구를 통해서 수집한다.
	- https://docs.google.com/presentation/d/1E0HUKbGFaGpGIyZFbQ5iyX-egynVwXqfGqwl42VE1g4/edit#slide=id.g27cc25ec5b_0_13
- JSON응답을 위해서 DB연동은 필요 없고, 서버에서 JSON형태를 routing처리를 통해서 만든다.

### 3. 기타 코드구현시 참고사항
- 코드구현전에 설계서를 자유포맷으로 작성하고, 이를 포함해서 제출한다(인증샷, 온라인문서링크 등 자유롭게 작성하고 제출)
- 모든 코드는 prorotytpe기반의 객체화를 기본으로 해서 구현한다.
- 함수는 크기가 적당하고, 재사용되도록 범용성을 고려해서 만든다. 
- 모든 코드는 클린코드를 지향한다.
- 동작결과가 크게 다르지 않다면, 결과 화면의 문구나 결과의 표현방법은 약간 다른 부분이 발생해도 상관없다.
- 요구사항이 잘못되었다고 판단되거나 이해가 안가는 부분은 스스로 판단해서 진행한다. (설명이 필요하면 주석으로 남긴다)
- 검색자동완성이 다른 서비스에서 사용할 수 있도록 전체 코드가 범용성있는 라이브러리 형태일수록 이상적이다.
- 커밋로그에 신경쓰고, 결과를 github에 올린다.
- 시간이 부족하면 되는데까지 구현하고 제출한다.어떤 부분을 포기할지는 본인이 스스로 임의로 결정한다.