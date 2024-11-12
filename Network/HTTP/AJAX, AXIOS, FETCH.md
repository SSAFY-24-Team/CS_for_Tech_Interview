## 🌀 AJAX (Asynchronous JavaScript and XML)

XMLHttpRequest 기술을 사용해 복잡하고 동적인 웹페이지를 구성하는 프로그래밍 방식

AJAX는 비동기적 웹 애플리케이션의 제작을 가능하게 하는 핵심 기술로, JavaScript를 사용하여 서버와 **비동기적으로** 데이터를 교환하고 조작할 수 있게 함.
이를 통해 웹 페이지의 **일부만을** 업데이트할 수 있으므로, 사용자는 더 빠르고 부드러운 웹 경험을할 수있음

### ✔️ AJAX의 작동 원리와 구현

AJAX의 핵심은 JavaScript의 XMLHttpRequest 객체를 사용하여 **서버와의 비동기 통신을 수행**하는 것

이를 통해 웹 페이지 전체를 새로 고침하지 않고도 필요한 데이터만을 서버로부터 받아와서 웹 페이지에 동적으로 표시할 수 있음

비동기 통신의 가장 큰 장점은 웹 애플리케이션의 반응성을 크게 향상시킨다는 점
사용자가 어떤 동작을 수행할 때마다 전체 페이지를 새로 고침할 필요 없이 필요한 부분만을 업데이트할 수 있기 때문에, 사용자 경험이 크게 개선됨

> AJAX는 웹 페이지의 일부만을 업데이트함으로써 사용자 경험을 크게 향상시키는 핵심 기술
> 비동기 통신을 통해 웹 애플리케이션의 반응성을 높이고, 사용자 대기 시간을 줄임으로써 보다 효율적이고 사용자 친화적인 웹 서비스 제공

<br />

## 🌀 AXIOS

브라우저와 node.js에서 사용할 수 있는 **Promise 기반 HTTP 클라이언트 라이브러리**
백엔드와 프론트엔드가 통신을 쉽게하기 위해 AJAX와 더불어 사용

비동기로 HTTP 통신을 할 수 있으며 return을 promise 객체로 해주기 때문에 response 데이터를 다루기 쉬움

### ✔️ AXIOS 특징

- 운영 환경에 따라 브라우저의 XMLHttpRequest 객체 또는 Node.js의 http api 사용
- Promise(ES6) API 사용
- 요청과 응답 인터셉트
- 요청 및 응답 데이터 변환
- HTTP 요청 취소
- HTTP 요청과 응답을 JSON 형태로 자동 변경
- XSRF를 막기위한 클라이언트 사이드 지원

<br />

## 🌀 FETCH

자바스크립트로 AJAX를 요청하는 방법 중 XMLHttpRequest() 객체를 생성하여 요청하는 방법이 있지만 문법이 난해하고 가독성도 좋지 않음

자바스크립트 AJAX 통신의 최신 기술인 `fetch()` 메서드가 있음 (JS 내장 라이브러리)

fetch API는 Promise 기반으로 구성되어 있어 비동기 처리 프로그래밍 방식에 잘 맞음. 그래서 then이나 catch와 같은 체이닝으로 작성할 수 있음

### ✔️ FETCH 특징

- 자바스크립트 내장 라이브러리이므로 별도로 import 할 필요 X
- Promise API 사용
- 내장 라이브러리이기 때문에 업데이트에 따른 에러 방지 가능
- 지원하지 않는 브라우저 존재
- JSON으로 변환해주는 과정 필요

### ✔️ AXIOS VS FETCH

![](https://velog.velcdn.com/images/jiwoni1/post/639f1a90-32ea-45fc-8b05-776e2084f140/image.png)

간단하게 사용할 때는 FETCH
확장성을 염두했을 때는 AXIOS가 좋다.

<details>
   <summary> AXIOS란 무엇인가요?</summary>
<br />

브라우저와 node.js에서 사용할 수 있는 Promise 기반 HTTP 클라이언트 라이브러리입니다. 백엔드와 프론트엔드가 통신을 쉽게하기 위해 AJAX와 더불어 사용합니다.

</details>
<details>
   <summary> AXIOS와 FETCH의 차이점은?</summary>
<br />

AXIOS는 써드파티 라이브러리로 별도의 설치가 필요하지만, FETCH는 JS 내장 라이브러리로 별도의 설치가 필요없습니다. 또한 AXIOS는 자동으로 JSON 형식으로 변환되지만 FETCH는 따로 메서드를 사용해서 변환해야합니다. AXIOS가 좀 더 많은 브라우저에 지원되고 FETCH는 지원하지 않는 브라우저가 존재합니다.

</details>

<br />

## 출처

[AXIOS 공식문서](https://axios-http.com/kr/docs/intro)  
[MDN AJAX](https://developer.mozilla.org/ko/docs/Glossary/AJAX)  
[프론트엔드 개발에서의 AJAX와 비동기 통신의 이해](https://f-lab.kr/insight/understanding-ajax-and-asynchronous-communication?gad_source=1&gclid=EAIaIQobChMI__ek1f3ViQMVU5G5BR3zKTmrEAMYASAAEgLmsfD_BwE)  
[AXIOS 설치 사용](https://inpa.tistory.com/entry/AXIOS-%F0%9F%93%9A-%EC%84%A4%EC%B9%98-%EC%82%AC%EC%9A%A9)  
[Fetch API 으로 AJAX 요청하기](https://inpa.tistory.com/entry/JS-%F0%9F%93%9A-AJAX-%EC%84%9C%EB%B2%84-%EC%9A%94%EC%B2%AD-%EB%B0%8F-%EC%9D%91%EB%8B%B5-fetch-api-%EB%B0%A9%EC%8B%9D)
