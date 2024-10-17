# NoSQL

### RDB의 단점

- 경직된 스키마
    - 행과 열의 2차원 테이블 형태에 데이터를 저장
    - 대량의 데이터를 가진 테이블의 스키마 변경 작업에 위험 부담이 크다 → 유연한 확장성 부족
- 과도한 join과 성능 하락
    - 중복 제거를 위해 정규화를 진행 → 여러 테이블의 복잡한 join으로 read 성능 하락
        
        ![image.png](/img/NoSQL/5.png)
        
- scale out 어려움
    - 기본적으로 한 대의 컴퓨터에 저장하지만, read/write 요청이 늘어나는 경우 DB 서버의 CPU와 메모리 사용량이 증가해 부하 증가
    - scale up을 통해 성능 향상은 가능
    - multi-master, sharding 방법이 있지만, 일반적으로 scale out에 유연하지 않음
    
    ![image.png](/img/NoSQL/1.png)
    
- transaction ACID로 인해 성능 영향
    - ACID를 보장하기 위해 DB 서버의 성능에 영향을 미침

### NoSQL 등장 배경

![image.png](/img/NoSQL/2.png)

- 인터넷 사용자 증가와 SNS 같은 글로벌 서비스 등장
- high throughput 및 low latency 요구
- 비정형 데이터의 증가

### NoSQL 개념

- Not only SQL
- SQL만을 사용하지 않는 데이터베이스 관리 시스템(DBMS)
- 비관계형 데이터베이스 유형

### NoSQL 종류

- mongoDB
- redis
- DynamoDB
- neo4j
- HBase
- CouchDB

![image.png](/img/NoSQL/3.png)

### NoSQL 특징

- 유연한 스키마
    - 데이터베이스에서 사전에 스키마를 정의하지 않고 데이터 저장
    - application 레벨에서 스키마 관리 필요
- 중복 허용(join 회피)
    - application 레벨에서 중복된 데이터들이 모두 최신 데이터를 유지할 수 있도록 관리 필요
- scale out에 최적화
    - 서버 여러 대로 하나의 클러스터를 구성하여 사용
    
    ![image.png](/img/NoSQL/4.png)
    
- high throughput 및 low latency 추구
    - ACID의 일부를 포기하는 대신 처리량과 응답시간 향상
    - 금융/결제/예약 시스템처럼 consistency가 중요한 환경에서는 사용하기 조심스러움

### 질의응답

<details>
   <summary> RDB와 NoSQL의 차이점은? (👈 Click)</summary>
1. RDB는 관계형으로 데이터를 저장하지만, NoSQL은 그렇지 않다. <br>
2. RDB는 정적 스키마를 가지고, NoSQL은 유연한 스키마 구조를 갖는다. <br>
3. RDB는 scale up이 용이하고, NoSQL은 scale out이 용이하다.

</details>
<br>

> 출처
> 

[https://www.youtube.com/watch?v=sqVByJ5tbNA&list=PLcXyemr8ZeoREWGhhZi5FZs6cvymjIBVe&index=31](https://www.youtube.com/watch?v=sqVByJ5tbNA&list=PLcXyemr8ZeoREWGhhZi5FZs6cvymjIBVe&index=31)<br>
[https://www.oracle.com/kr/database/nosql/what-is-nosql/](https://www.oracle.com/kr/database/nosql/what-is-nosql/)<br>
[https://ud803.github.io/데이터베이스/2021/11/16/RDB-vs.-NoSQL-언제-누구를-써야할까/](https://ud803.github.io/%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4/2021/11/16/RDB-vs.-NoSQL-%EC%96%B8%EC%A0%9C-%EB%88%84%EA%B5%AC%EB%A5%BC-%EC%8D%A8%EC%95%BC%ED%95%A0%EA%B9%8C/)
