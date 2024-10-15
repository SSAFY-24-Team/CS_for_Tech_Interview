# DBCP(Database Connection Pool)

![스크린샷 2024-10-15 오후 1.32.01.png](/img/DBCP/1.png)

- 백엔드 서버와 DB 서버가 쿼리를 요청하고 주고 받는 것은 TCP 기반 네트워크 통신
- 각 요청마다 connection을 열고 닫는 시간적인 비용 발생
- 수많은 사용자가 요청했을 때 서버 과부화 문제가 생길 수 있다.
- 이러한 문제를 효율적으로 해결한 것이 DBCP

![스크린샷 2024-10-15 오후 1.34.54.png](/img/DBCP/2.png)

- DBCP란 데이터베이스와의 연결을 관리하기 위한 커넥션 풀 라이브러리
- WAS를 띄울때 DB 서버와의 connection을 미리 맺어 pool에 저장한 후, 요청이 들어오면 connection을 가져와서 사용하고 응답이 끝나면 pool에 다시 반납한다.
- 즉, connection을 재사용해 시간적인 비용을 최소화할 수 있다.

---

### DB 서버(MySQL) 설정 방식

- max_connections
    - client와 맺을 수 있는 최대 connection 수
    - DBCP의 최대 connection 수가 같은 경우 백엔드 서버의 스케일 아웃에 문제가 발생
        
        ![스크린샷 2024-10-15 오후 2.02.22.png](/img/DBCP/3.png)
        
- wait_timeout
    - connection이 inactive 할 때 다시 요청이 오기까지의 대기 시간을 설정
    - 요청이 도달하면 대기 시간은 0으로 초기화
    - 설정된 대기 시간을 초과하면 MySQL에서 연결을 해제

### DBCP(HikariCP) 설정 방식

- minimumIdle
    - pool에서 최소한의 idle connection 수
    - 기본값은 maximumPoolSize와 동일
- maximumPoolSize
    - pool이 가질 수 있는 최대 connection 수
    - idle과 active(in-use) connection 합쳐서 최대 수
- idle connection < minimumIdle & 전체 connection 수 < maximumPoolSize 인 경우는 새로운 idle connection을 생성함
- maxLifeTime
    - pool에서 connection의 최대 수명
    - maxLifetime을 넘기면 idle 상태의 connection일 경우 pool에서 바로 제거
    - active 상태의 connection일 경우 pool로 반환된 후 제거
- connectionTimeout
    - pool에서 connection을 받기 위한 대기 시간
    - 대기 시간을 초과하면 에러 발생

### 예제 질문
<details>
   <summary> DBCP 사용 이유는? (👈 Click)</summary>
- WAS와 DB 서버의 connection을 재사용해 시간적인 비용을 최소화하기 위함

</details>

> 출처
> 

[https://www.youtube.com/watch?v=zowzVqx3MQ4&list=PLcXyemr8ZeoT-_8yBc_p_lVwRRqUaN8ET&index=62](https://www.youtube.com/watch?v=zowzVqx3MQ4&list=PLcXyemr8ZeoT-_8yBc_p_lVwRRqUaN8ET&index=62)