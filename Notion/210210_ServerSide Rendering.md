- [ServerSide Rendering](#serverside-rendering)
  - [서버사이드 랜더링의 역사](#서버사이드-랜더링의-역사)
    - [1. Static Sites](#1-static-sites)
    - [2. iframe](#2-iframe)
    - [3. XMLHttpRequest](#3-xmlhttprequest)
    - [4. AJAX](#4-ajax)
    - [5. CSR - Client Side Rendering](#5-csr---client-side-rendering)
      - [CSR 의 문제점](#csr-의-문제점)
    - [6. SSR - Server Side Rendering](#6-ssr---server-side-rendering)
      - [SSR 의 장단점](#ssr-의-장단점)
    - [7. SSG - Static Stite Generation](#7-ssg---static-stite-generation)

# ServerSide Rendering

## 서버사이드 랜더링의 역사

### 1. Static Sites
클라이언트가 url을 요청하면 서버에 이미 저장되어있는 HTML 문서를 받아 보여주는 형식

페이지 내에서 다른 링크를 클릭할 경우, 다시 서버에 페이지를 재요청하여 페이지 전체가 업데이트 되어야 하는 구조

1990 년대 중반까지 이용했으나, 사용성 면에서 좋지 않음

### 2. iframe
1996 년 부터 페이지 내에서 또 다른 문서를 불러올 수 있는 iframe 이 도입되면서 페이지내에서 부분적으로 문서를 받아와 업데이트할 수 있게 됨

### 3. XMLHttpRequest
1998 년 이후 부턴 fetch API의 시초, XMLHttpRequest API가 개발되어

HTML전체가 아닌, `json` 형태로  서버에서 가볍게 데이터만 받아올 수 있게 됨.
해당 `json` 파일을 JS로 파싱하여 HTML에 동적으로 업데이트하는 방식을 사용

### 4. AJAX
2005 년 부터 싱글 페이지 애플리케이션 (Single Page Application - SPA) 을 이용하게 됨

사용자가 한개의 페이지에 머물러서 필요한 데이터를 부분적으로만 서버에 요청하여 해당 부분만 업데이트 함 - 사용성 매우 좋음

### 5. CSR - Client Side Rendering 
사용자들의 PC 성능이 점차 좋아지고 JS 표준화도 안정화 됨에 따라서 프레임워크(React, Angular, Vue...) 들이 출시됨

서버에서 간단한 HTML 파일을 보내주면 해당 관련된 js 파일을 보내주어 앱에 필요한 소스 코드를 함께 내려받게 되는데,
이때 데이터를 가지고있는 `json` 파일을 함께 내려받아 해당 HTML에 모두 그려주게 됨

#### CSR 의 문제점

1. 사용자가 첫 화면을 볼 때 시간이 오래걸릴 수 있다는 점
2. 좋지 않은 SEO - Search Engine Optimization 를 가지게 됨
> 구글, 네이버 등 큰 플랫폼의 검색엔진은 웹사이트의 HTML을 분석하여 검색할 때 정보를 얻는데, HTML이 텅 비어있어 검색에 필요한 데이터를 수집 할 수 없게됨

### 6. SSR - Server Side Rendering
기존 Static Site에서 영감을 받아, 웹사이트에 접속하면 서버에서 필요한 데이터를 모두 가져와서, HTML 파일을 만들고,
HTML 파일을 동적으로 제어할 수 있는 소스코드를 클라이언트에게 보내줌. 그러면 클라이언트 측에서 잘 만들어진 HTML 문서를 받아와 바로 사용자에게 보내줌

#### SSR 의 장단점
* 장점 : 첫 번째 로딩이 빨라짐. 모든 컨텐츠가 HTML에 담겨져있기 때문에 조금 더 나은 SEO가 가능
* 문제점 : Static Site에 존재했던 깜빡임 문제 (Blinking Issue) 가 존재

> 사용자가 클릭시 전체적인 웹사이트를 다시 서버에서 받아오는 것과 동일하기 때문에 별로 좋지 않은 UX를 경험할 수 있고, 서버에 과부하가걸릴 수 있음 <br>
사용자가 빠르게 웹사이트를 볼 수는 있지만, 그 후 스크립트를 내려받기 때문에 사용자가 요소를 클릭했을 때 반응이 없는 경우도 있을 수 있음
<br> 필수로 고려해야할 :: <b>사용자가 화면을 볼 수 있는 시간 TTV(Time To View)과, 사용자가 인터랙션을 할 수 있는 TTI (Time To Interact)</b>가 길어지게 됨
 
### 7. SSG - Static Stite Generation
`React + Gatsby` 라이브러리는 정적으로 웹 페이지 생성을 해놓아 서버에 미리 배포해둘 수 있음. 마냥 정적이진 않은데, index 파일에 js도 함께 포함되기 때문에 동적인 요소를 가지고 있음
`React + Next.js` 라이브러리는 다양한 방식으로 렌더링해줌

-------------------

