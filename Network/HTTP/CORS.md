## 💻CORS 에러란?

![](/img/CORS/1.png)

#### CORS 에러란 무엇일까요?

일단, CORS는 `Cross-Origin-Resource-Sharing` 이라는 뜻입니다. 번역하면, **교차 출처 리소스 공유** 이지요. `출처`가 교차한다는게 무슨 뜻일까요?

<br />

### 🫧Origin (출처)

---

![](/img/CORS/2.png)

이 그림은 URL의 구성 요소를 나타내는 그림입니다.
`Protocol` + `Host` + `Port` = `Origin`
이 세 개가 합쳐진게 바로 **Origin** 이죠.

이 중 한 가지라도 다르다면, 다른 출처가 되게 됩니다.

> 참고로 출처 비교와 차단은 **브라우저**가 합니다.

<br />

### 🫧 SOP 정책

---

출처에 대해 알아보았으니, 동일 출처 정책에 대해 알아보겠습니다.

> **SOP(Same Origin Policy)**
> 동일한 출처에서만 리소스를 공유할 수 있음

동일 출처 서버에 있는 리소스는 자유롭게 가져올 수 있지만, 다른 출처 서버에 있는 리소스는 가져올 수 없음을 의미합니다.

#### SOP 정책이 필요한 이유

동일 출처만 가능하고 왜 다른 출처는 막아놓았을까요?
과거에는 프론트엔드와 백엔드를 따로 구성하지 않고 한 번에 구성해서 모든 처리가 같은 도메인 안에서 가능했습니다. 그래서 다른 출처로 요청을 보내는 게 의심스러운 행위로 보일 수밖에 없었죠.

실제로 SOP 정책이 없다면, 해커가 CSRF(Cross-Site Request Forgery)나 XSS(Cross-Site Scripting) 등의 방법을 이용해서 우리가 만든 어플리케이션에서 해커가 심어놓은 코드가 실행하여 개인 정보를 가로챌 수 있습니다.

하지만 시간이 지난 지금은 클라이언트에서 API를 직접 호출하는 방식이 당연해졌습니다. 그런데 보통 클라이언트와 API는 다른 도메인에 있는 경우가 많죠. 그래서 CORS 정책이 생기게 되었습니다. 출처가 다르더라도 요청과 응답을 주고받을 수 있도록 서버에 리소스 호출이 허용된 출처(Origin)를 명시해 주는 방식으로말이죠.

<br />

### 🫧 CORS

---

위에서 말한 것 처럼, CORS는 다른 출처의 리소스 공유에 대한 허용/비허용 정책입니다. 다른 서버의 API를 이용해야하는 상황에서 다른 출처라도 리소스를 받아들이기 위해서죠.

#### 브라우저의 CORS 기본 동작 원리

1. 클라이언트에서 다른 출처로 리소스를 요청할 때, HTTP 요청의 헤더에 Origin을 담아서 전달합니다.

```js
Origin: https://velog.io/@jiwoni1
```

2. 서버는 이 요청에 대한 응답을 할 때, 응답헤더의 Access-Control-Allow-Origin라는 값에 접근이 허용된 출처을 담아 클라이언트로 전달합니다.
3. 클라이언트에서 Origin과 서버가 보내준 Access-Control-Allow-Origin을 비교합니다. 같다면 허용, 다르다면 CORS 에러를 발생시키는 것입니다.
   <br />

### 🫧 CORS 에러 해결법

---

위 내용에 따르면 CORS 에러를 해결하려면 `서버에서 Access-Control-Allow-Origin 헤더에 허용할 출처를 기재해서 클라이언트에 응답`하면 문제가 해결되는 것입니다!

#### ▪️ 서버에서 Access-Control-Allow-Origin 응답 헤더 세팅하기

서버에서 Access-Control-Allow-Origin 헤더를 설정해서 요청을 수락할 출처를 명시적으로 지정할 수 있습니다. 이 헤더를 세팅하면 출처가 다르더라도 `https://velog.io/@jiwoni1`의 리소스 요청을 허용하게 됩니다.

```java
'Access-Control-Allow-Origin': <origin> | *
```

`*`를 설정하면 출처에 상관없이 리소스에 접근할 수 있는 와일드카드이기 때문에 보안에 취약해집니다. 그래서 `Access-Control-Allow-Origin': https://velog.io/@jiwoni1`과 같이 직접 허용할 출처를 세팅하는 방법이 더 좋습니다.  
<br />

#### ▪️ 프록시 서버 사용하기

클라이언트가 리소스를 직접적으로 요청하는 대신, 프록시 서버를 사용하여 웹 애플리케이션에서 리소스로의 요청을 전달하는 방법도 있습니다. 이 방법을 사용하면, 클라이언트 리소스와 동일한 출처에서 요청을 보내는 것처럼 보이므로 CORS 에러를 방지할 수 있습니다.

> **프록시 서버**  
> Proxy는 **대리**, **대신**이라는 뜻  
> 클라이언트가 프록시 서버 자신을 통해서 다른 네트워크 서비스에 간접적으로 접속할 수 있게 해줍니다.  
> 즉, 브라우저와 서버 간의 통신을 도와주는 `중계서버`입니다.
> ![](/img/CORS/3.png)

**예를 들어, 요청해야하는 `http://example.com`라는 주소의 클라이언트가 `http://api.example.com`에 데이터를 요청하는 상황이라면...**

클라이언트는 직접적으로 리소스에 요청하는 대신, `http://example-proxy.com`라는 프록시 서버에 요청을 보낼 수 있습니다.  
그러면 프록시 서버가 `http://api.example.com`으로 요청을 전달하고, 응답을 다시 클라이언트에 반환합니다.  
이렇게 하면 요청이 `http://example-proxy.com`보내진 것처럼 보이므로, CORS 에러를 피할 수 있습니다.

### 예상 면접 질문

<details>
   <summary> CORS는 무엇인가요? </summary>
<br />

CORS는 `Cross-Origin-Resource-Sharing` 으로, 다른 출처에서 리소스를 가져오고자 할 때 리소스 공유에 대한 허용/비허용 정책입니다.

</details>

<br />
<details>
   <summary> CORS 에러를 해결하는 방법은 무엇인가요? </summary>
<br />

서버에서 Access-Control-Allow-Origin 헤더를 설정해서 요청을 수락할 출처를 지정하는 방법과 프록시 서버를 사용해서 동일 출처인 것처럼 보이게 하는 방법이 있습니다.

</details>
<br />

### 💌출처

[악명 높은 CORS 개념 & 해결법 - 정리 끝판왕 ](https://inpa.tistory.com/entry/WEB-%F0%9F%93%9A-CORS-%F0%9F%92%AF-%EC%A0%95%EB%A6%AC-%ED%95%B4%EA%B2%B0-%EB%B0%A9%EB%B2%95-%F0%9F%91%8F)

[토스 페이먼츠-결제창에서 CORS 대응하기](https://docs.tosspayments.com/blog/payment-window-cors-error)

[CORS 가 뭔데 CORS 에러 어떻게 해결하는건데](https://velog.io/@jh100m1/CORS-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%AD%94%EB%8D%B0-%EC%96%B4%EB%96%BB%EA%B2%8C-%ED%95%B4%EA%B2%B0%ED%95%98%EB%8A%94%EA%B1%B4%EB%8D%B0)
