react가 render(코드를 브라우저가 이해하는 html로)되는 방식은 client side rendering
=> 브라우저(클라이언트 측)가 rendering 작업을 함
클라이언트는 자바스크립트를 로드하고, 자바스크립트가 UI를 빌드함
즉 브라우저의 JS 엔진에 의해 컴포넌트가 추가됨
따라서 로딩이 필연적으로 생김
그리고 검색 엔진은 이 파일을 빈 파일로 봄

next가 render되는 방식은 server side rendering
서버에서 render 되고 그 html을 response로 줌
즉 페이지를 바로 볼 수 있음
Next에서 모든 컴포넌트와 페이지들은 먼저 서버에서 render됨
("use client"와 관계 없이)

Hydration
단순 HTML을 React application으로 초기화하는 작업

사용자가 어떤 경로에 접근했을 때 일단 HTML 먼저 띄워주고(SSR) 그 후에 hydration

"use client"
backend에서 render되고 fontend에서 hydrate 하겠다.

"use client"를 사용하지 않으면 server component라는 뜻
=> 클라이언트에게 전달되지 않음. API 키 등 사용 가능

layout은 중첩됨
metadata는 server component에만 있을 수 있고 병합됨

Next에서는 fetch하면 응답을 알아서 캐싱함.
첫 access만 로딩 필요(API hit). 이후 접근은 캐시된 데이터로 로딩 없음(no API hit).
근데 최신 데이터가 필요한 순간이 있을 수 있음.
=> 캐싱, revalidation 알아보기

Promise.all을 사용하여 병렬 fetch 가능
근데 Promise.all 내부에 있는 함수들이 모두 끝나야 확인 가능
=> Suspense 사용해서 따로 따로 render 가능
fallback은 Suspense 내부의 컴포넌트가 render되기 전 보여줄 컴포넌트

NextJS 특수 파일
page.tsx
error.tsx
loading.tsx
not-found.tsx
layout.tsx
