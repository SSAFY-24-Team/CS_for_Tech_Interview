# DB 분산 저장 기법

# 배경

- 서비스의 크기가 커지고 데이터베이스의 볼륨이 커질수록, 용량의 한계와 성능 저하로 인한 병목 지점이 발생한다.
- 이러한 이슈 해결을 위해 데이터베이스를 분할하고 거대한 데이터셋을 서브셋으로 분리하여 관리하는 방법이 필요하다.

# 파티셔닝(Partitioning)

### 개념

- table을 더 작은 table들로 나누는 것
- 큰 테이블을 partition이라는 작은 단위로 물리적 분할
- 사용자는 하나의 테이블에 접근하는 것과 동일하게 사용 가능

### 장단점

- 장점
    - partition 단위 백업, 추가, 삭제 변경 → 데이터 가용성 향상
    - 데이터 전체 검색 시 필요한 부분만 탐색 → 데이터 접근 범위를 줄여 성능 향상
- 단점
    - table간 join 비용 증가
    - index 관리 비용 증가(table과 index를 별도로 파티셔닝할 수 없음)

### 종류

- 수직(vertical) 파티셔닝
    - column을 기준으로 table을 나누는 방식
    - 자주 사용하는 컬럼 등을 분리시켜 성능 향상
    - 전체 데이터 필요시 join을 사용해 동작
    
    ![image.png](/img/DB_분산저장기법/0.png)
    
- 수평(horizontal) 파티셔닝
    - row를 기준으로 table을 나누는 방식
    - 스키마가 같은 데이터를 두 개 이상의 테이블에 partition key를 기준으로 나누어 저장
    - 데이터의 개수와 index의 크기가 줄어들어 성능 향상
    - 데이터를 찾는 과정이 기존보다 복잡하기 때문에 latency 증가
    
    ![image.png](/img/DB_분산저장기법/1.png)
    

### 파티셔닝의 분할 기준

![image.png](/img/DB_분산저장기법/2.png)

- 범위 분할(Range Partitioning)
    - 데이터 값을 특정 범위 기준으로 분할
- 목록 분할(List Partitioning)
    - 데이터 값이 특정 목록에 포함된 경우 분할
- 해시 분할(Hash Partitioning)
    - 특정 컬럼의 값을 해싱하여 분할
- 합성 분할(Composite Partitioning)
    - 상기 기술을 결합해 사용하는 방식

# 샤딩(Sharding)

### 개념

- 수평(horizontal) 파티셔닝의 일종으로 데이터를 서로 다른 DB 서버에 분산하여 저장한다.
- 동일한 스키마를 가지고 있는 여러 대의 DB 서버에 shard라는 작은 단위로 물리적 분할
- 파티셔닝의 partition key가 shard key로 대응됨
- 데이터베이스 차원의 수평 확장(scale out)

![image.png](/img/DB_분산저장기법/3.png)

### 장단점

- 장점
    - DB 서버 부하 분산 효과
    - 쿼리 성능 향상
- 단점
    - 여러 shard에 걸친 데이터 join의 어려움

# 리플리케이션(Replication)

### 개념

- DB를 복제해서 여러 대의 DB 서버에 저장하는 방식
- 두 개 이상의 DBMS 시스템을 Master / Slave로 나눠서 동일한 데이터를 저장하는 방식

![image.png](/img/DB_분산저장기법/4.png)

### 장단점

- 장점
    - 서버 부하 감소 → Read 성능 향상 효과
    - 안정성 및 가용성 향상 → 장애 복구 및 복구 시간 단축
- 단점
    - 일관성 충돌 → 일시적인 데이터 불일치 현상
    - 추가적인 리소스 필요 → 비용 증가

# 예제 질문
<details>
   <summary> 파티셔닝과 샤딩의 가장 큰 차이점은? (👈 Click)</summary>
- 파티셔닝은 단일 DB 서버에서 여러 table로 데이터를 분할하지만, 샤딩은 여러 DB 서버를 사용해 분산 저장한다.

</details>

> 참고자료
>
[https://gmlwjd9405.github.io/2018/09/24/db-partitioning.html](https://gmlwjd9405.github.io/2018/09/24/db-partitioning.html)
<br>
[https://hudi.blog/db-partitioning-and-sharding/](https://hudi.blog/db-partitioning-and-sharding/)
<br>
[https://www.youtube.com/watch?v=P7LqaEO-nGU&list=PLcXyemr8ZeoT-_8yBc_p_lVwRRqUaN8ET&index=61](https://www.youtube.com/watch?v=P7LqaEO-nGU&list=PLcXyemr8ZeoT-_8yBc_p_lVwRRqUaN8ET&index=61)
<br>
[https://medium.com/@byeongsoon94/데이터베이스-리플리케이션-replication-이란-무엇인가-24f7c22fe74c](https://medium.com/@byeongsoon94/%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4-%EB%A6%AC%ED%94%8C%EB%A6%AC%EC%BC%80%EC%9D%B4%EC%85%98-replication-%EC%9D%B4%EB%9E%80-%EB%AC%B4%EC%97%87%EC%9D%B8%EA%B0%80-24f7c22fe74c)