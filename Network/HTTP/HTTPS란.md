# 💡HTTPS란?

## ▪️ HTTPS의 정의

> **HTTPS (Hypertext Transfer Protocol Secure)**
> HTTP의 더 안전한 버전

> 애플리케이션 계층과 전송 계층 사이에 신뢰 계층인 SSL/TLS 계층을 넣은 신뢰할 수 있는 HTTP 요청
> ➜ `통신을 암호화`

![](./HTTPS란/HTTPS1.jpg)

![](./HTTPS란/HTTPS2.png)

## ▪️ **SSL / TLS**

> Secure Socket Layer / Transport Layer Security
> ➜ **전송 계층에서 보안을 제공하는 프로토콜**
> SSL이 버전이 올라가며 TLS로 명칭이 변경된 것 (현재는 대다수의 보안 프로토콜이 TLS로 교체되어 더 이상 SSL을 사용하지 않지만, 이름만 이렇게 부름)

> 클라이언트와 서버가 통신을 할 때 SSL/TLS를 통해 제3자 메시지를 도청하거나 변조하지 못하도록함 (데이터를 암호화)

![](./HTTPS란/HTTPS3.jpg)

### SSL

> 공개 키 및 개인 키를 이용한 암호화 및 복호화를 통해 보안을 제공

### TLS

> 현재 주로 사용되는 프로토콜, 더 강력한 보안 및 암호화 기술을 도입, SSL의 취약점을 보완하여 보다 안전한 통신 제공

## ▪️ SEO와 HTTPS

> **SEO(Search Engine Optimization)** 검색엔진 최적화
> 검색 엔진으로 웹 사이트를 검색했을 때 그 결과를 페이지 상단에 노출시켜 많은 사람이 볼 수 있도록 최적화하는 방법을 의미

구글은 HTTPS 서비스를 하는 사이트가 그렇지 않은 사이트보다 SEO 순위가 높을 것이라고 공식적으로 밝힘
➜ SEO를 위해서는 HTTPS 서비스를 하는 것이 서비스 운영 측면에서 좋음

## ▪️ HTTP와 HTTPS의 차이

### 보안

**- HTTP** : 비안전한 프로토콜, 데이터는 암호화되지않고 평문으로 전공
interceptor 또는 데이터 변조에 취약, 데이터 무결성 보장X
**- HTTPS** : 데이터를 암호화, 보안 강화를 위해 SSL/TLS 프로토콜을 사용, interceptor 방지, 데이터 무결성 보장

### 포트 번호

**- HTTP** : 기본적으로 80번 포트
**- HTTPS** : 기본적으로 443번 포트

### 인증서

**- HTTP** : 인증서가 필요X
**- HTTPS** : 서버는 클라이언트에게 인증서를 제공하고, 클라이언트는 이를 사용하여 서버의 신원을 확인

### ❓면접 예상 질문

<details>
   <summary>HTTP보다 HTTPS를 선택하는 이유는 무엇인가요?</summary>
   
    HTTPS는 모든 데이터를 암호화된 형태로 전송하므로 데이터 무결성을 보장할 수 있습니다. 또한, 검색 엔진 최적화에도 도움이 됩니다.
<br />
</details>   
<br />

#### 출처

https://blog.naver.com/jhc9639/222702936704
https://prmblogs.tistory.com/56
https://f-lab.kr/insight/basic-http-https-for-frontend-developers
https://rachel-kwak.github.io/2021/03/08/HTTPS.html
