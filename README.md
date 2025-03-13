# 프론트엔드 개발 완성도 체크리스트

한국어 | [English](./README-EN.md)

## 개요
바쁘게 작업을 하다보면 가끔씩 놓치는 부분들이 있습니다. 그럴 땐 빠르게 작업 후 한꺼번에 확인하고 수정하는 것이 효율적일 때가 있습니다. <br/>
작업 후 완성도 확인을 위해 개인적으로 사용하던 체크리스트를 공유하고자 합니다.  <br/><br/>
업무 및 스터디를 통해 쌓은 경험을 바탕으로 작성되었으며, 계속해서 업데이트 될 예정입니다. :) <br/>
피드백이 필요하거나 추가하고 싶은 내용이 있으시면 언제든지 말씀주세요 🙌

## 체크리스트
### 1. 성능
- [ ] lighthouse를 통한 성능 측정해보기
- [ ] 이미지 최적화
    - [ ] 사용할 이미지 크기보다 큰 이미지를 불러오고 있지는 않은가?
    - [ ] 지연로딩이나 사전로딩이 가능한 상황인가?
    - [ ] webp 형식을 사용할 수 있는가? (브라우저 호환성을 위한 대체 이미지도 함께 제공)
- [ ] 애니메이션 최적화
    - [ ] will-change나 translate3d 속성을 사용하여 미리 레이어를 분리해도 되는가?
    - [ ] 불필요한 reflow나 repaint를 일으키는 속성은 없는가?
- [ ] 번들 사이즈
  - [ ] 번들 사이즈 측정해보기 (webpack-bundle-analyzer 등)
  - [ ] 코드 스플리팅이 필요한 부분은 있는가?
  - [ ] 부분 import 등으로 트리셰이킹이 가능한가?
  - [ ] svgr 파일을 svgo로 최적화하여 번들 사이즈를 줄일 수 있는가?
- [ ] 연산이 많은 변수/함수 최적화 
  - [ ] useMemo, useCallback을 사용하여 최적화할 수 있는 부분은 있는가?
- [ ] 렌더링 최적화 
  - [ ] 객체나 함수를 하위 컴포넌트에 props로 넘겨줄 때, 불필요한 렌더링이 일어나는 부분은 없는가?
  - [ ] 불필요한 렌더링을 막기 위해 React.memo 등을 사용할 수 있는가?
  - [ ] 전역 상태 관리 라이브러리를 사용할 때, 불필요한 렌더링이 일어나는 부분은 없는가? 
  - [ ] 초기 로드 성능을 위해 lazy loading이나 코드 스플리팅을 적용할 수 있는가?
  - [ ] 컴포넌트가 충분히 작은 단위로 분리되어 있지 않아 state 변경 시 불필요한 리렌더링이 일어나는 부분은 없는가? 
- [ ] 렌더링 방식 최적화
  - [ ] SSR/SSG/CSR/ISR 등을 적절히 사용하여 렌더링 방식을 최적화할 수 있는가?
- [ ] 폰트 최적화
  - [ ] font-display 속성을 사용하여 폰트 로딩 방식을 최적화할 수 있는가?
  - [ ] 폰트 파일을 최소화하여 사용할 수 있는가?
  - [ ] 최적화된 폰트 파일 포맷을 사용하고 있는가? (브라우저 호환성을 위한 대체 폰트도 함께 제공)

### 2. 사용성
- [ ] input 요소 사용성 향상
  - [ ] input에 inputmode를 따로 적용할 부분이 있는가? (ex 모바일 숫자 키패드)
  - [ ] input에 pattern을 적용하여 사용자가 입력할 수 있는 문자열을 제한할 수 있는가?
  - [ ] input에 placeholder를 적절히 사용하여 사용자가 입력해야 할 내용을 명확히 할 수 있는가?
- [ ] debounce나 throttle을 사용하여 사용성을 향상시킬 수 있는가?
  - [ ] debounce 적용이 가능한가? 검색 기능(useDeferredValue 조합), 버튼 중복 클릭 방지, 윈도우 리사이징, 자동 저장, 드래그 앤 드롭 등
  - [ ] throttle 적용이 가능한가? 스크롤이나 마우스 이벤트 처리 등
- [ ] 모바일 브라우저 지원 범위(제가 고려하는 기준으로 작성했습니다 (ios 13 이상, android 8.0(chrome 68) 이상)
  - [ ] flex의 gap 속성을 사용중인가? (@supports를 통해 polyfill 제공)
  - [ ] 외에 지원 범위를 벗어나는 브라우저 API나 css를 사용중인가? ([can i use](https://caniuse.com/)를 통해 확인)
- [ ] 사용자 피드백
  - [ ] API 호출 시 로딩 상태를 사용자에게 제공하고 있는가?
    - [ ] Suspense를 사용할 수 있는가?
    - [ ] 로딩 UI가 너무 빠르게 전환되지 않도록 기본 지연 타임을 설정할 수 있는가?
  - [ ] API 호출 시 에러 상태를 사용자에게 제공하고 있는가?
    - [ ] 400번대, 500번대 에러를 구분하여 사용자에게 알맞은 메시지를 제공하고 있는가?
    - [ ] 에러바운더리를 사용할 수 있는가?
  - [ ] 존재하지 않는 페이지로 이동 시 사용자에게 알맞은 메시지를 제공하고 있는가?

### 3. 웹 접근성
- [ ] [접근성 검사도구](https://catstanets.tistory.com/167)를 통해 웹 접근성을 확인해보기
- [ ] 키보드 접근성
  - [ ] 모든 기능을 키보드로 조작할 수 있는가?
  - [ ] 키보드 포커스가 확실하게 보이는가?
- [ ] 아이콘이나 이미지로만 되어있는 버튼에 aria-label을 적용하였는가?
- [ ] alt 태그가 적절하게 작성되어 있는가? [참고 링크](https://catstanets.tistory.com/142)
- [ ] skip to content 링크를 제공하여 사용자가 콘텐츠로 바로 이동할 수 있는가? [참고 링크](https://catstanets.tistory.com/152)
- [ ] aria-expanded, role 등 접근성을 고려하여 컴포넌트를 구현하였는가? [참고 링크](https://github.com/scottaohara/accessible_components)
- [ ] 버튼이 접근성 트리에서 누락되지 않도록 disabled 대신 aria-disabled를 사용하였는가?
- [ ] 모달을 esc 키로 닫을 수 있는가?
- [ ] block 처럼 접근성 트리에서 요소를 지워버리는 속성을 사용하지 않았는가?
- [ ] .sr-only 클래스를 사용하여 스크린 리더 사용자를 위한 정보를 제공하였는가? [참고 링크](https://catstanets.tistory.com/148)

### 4. 코드 개선
- [ ] 너무 많은 일을 하고 있는 함수가 있는가?
- [ ] 너무 많은 일을 하고 있는 컴포넌트가 있는가?
- [ ] 컴포넌트가 너무 크지 않은가?
- [ ] hook으로 분리할 수 있는 부분은 있는가?
- [ ] 중복되는 코드가 있는가?
- [ ] 함수나 변수명이 명확한가?