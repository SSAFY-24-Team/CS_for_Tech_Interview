# Web Server / WAS(Web Application Server)

# Web Server

![image.png](/img/Web_Server와_WAS/0.png)

### 개념

- 하드웨어 관점
    - Web Server가 설치되어 있는 컴퓨터
- 소프트웨어 관점
    - 웹 브라우저 클라이언트로부터 HTTP 요청을 받아 정적인 컨텐츠를 제공하는 프로그램

### 특징

- HTTP 프로토콜 기반으로 클라이언트의 요청에 대한 서비스 제공
- 주요 기능
    - 정적인 컨텐츠 제공
        - WAS를 거치지 않고 빠르게 자원 제공
    - 동적인 컨텐츠 제공을 위한 요청 전달
        - 클라이언트의 요청(Request)를 WAS에 보내고, WAS가 처리한 결과를 클라이언트에 전달(응답)

### 예시

- Apache Server
- Nginx
- IIS(Windows 전용 Web Server)

# WAS(Web Application Server)

![image.png](/img/Web_Server와_WAS/1.png)

### 개념

- DB조회나 다양한 로직 처리를 요구하는 동적인 컨텐츠 제공을 위해 만들어진 Application Server
- HTTP를 통해 컴퓨터나 장치에 어플리케이션을 수행해주는 미들웨어
- Web Server + Web Container

### 특징

- 동적 컨텐츠 제공을 통해 자원을 효율적으로 사용
- Web Server 기능들을 구조적으로 분리해 처리
    - 주로 DB 서버와 같이 수행
    - 분산 트랜잭션, 보안, 메시징, 쓰레드 처리 등의 기능을 처리하는 분산 환경에서 사용
- WAS가 가지고 있는 Web Server도 정적인 컨텐츠를 처리하는 데 성능상 큰 차이가 없다.
- 주요 기능
    - 프로그램 실행 환경과 DB 접속 기능 제공
    - 여러 개의 트랜잭션 관리 기능
    - 비즈니스 로직 수행

### 예시

- Tomcat
- JBoss
- Jeus
- Web Sphere

# Web Server와 WAS를 분리하는 이유

![image.png](/img/Web_Server와_WAS/2.png)

<aside>
💡

자원 이용의 효율성 및 장애 극복, 배포 및 유지보수의 편의성 증가

</aside>

- 기능을 분리해 서버 부하 방지
    - 다양한 로직 처리 수행에 바쁜 WAS와 단순한 정적 컨텐츠 처리를 위한 Web Server로 분리해 클라이언트에 빠른 서비스 제공
    - WAS만을 사용한다면 정적 데이터 처리로 인한 부하가 커지고, 동적 컨텐츠의 처리가 지연됨
- 물리적 분리로 보안 강화
    - SSL에 대한 암복호화 처리에 Web Server 사용
- 여러 대의 WAS 연결 가능
    - Load Balancing를 위해 Web Server 사용
    - fail over, fail back 처리에 유리
    - 여러 개의 서버 사용시 무중단 운영을 위한 장애 극복에 쉽게 대응 가능
        - 오류가 발생한 WAS를 이용하지 못하도록 앞 단의 Web Server에서 설정 후, WAS를 재시작하여 사용자가 오류를 느끼지 못하고 이용하도록 구성
    
    ![image.png](/img/Web_Server와_WAS/3.png)
    

# 예제 질문
<details>
   <summary> Web Server와 WAS의 차이점은? (👈 Click)</summary>
Web Server의 경우에는 정적 컨텐츠(HTML, CSS, 이미지 등) 처리에 특화되어 있으며, 클라이언트의 요청을 단순히 리소스로 매핑해 응답합니다.<br> 
WAS의 경우에는 동적 컨텐츠 처리에 특화되어, 비즈니스 로직 수행과 DB 조회 등 복잡한 연산을 처리합니다.


</details>
<br>

> 참고 자료
>
[https://gmlwjd9405.github.io/2018/10/27/webserver-vs-was.html](https://gmlwjd9405.github.io/2018/10/27/webserver-vs-was.html)
<br>
[https://dkswnkk.tistory.com/503](https://dkswnkk.tistory.com/503)