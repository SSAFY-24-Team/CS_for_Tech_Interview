# 트랜잭션(Transaction)

![image.png](/img/Transaction/0.png)

### 개념

- 데이터베이스의 상태를 변경시키기 위해 수행하는 논리적인 작업 단위
- 더 이상 분할이 불가능한 업무처리의 단위
- 한꺼번에 수행되어야 할 일련의 연산모음

### 특징

![image.png](/img/Transaction/2.png)

- ACID - 데이터베이스의 일관성과 무결성을 보장
    - 원자성(Atomicity)
        - 트랜잭션이 데이터베이스에 모두 반영되던가, 아니면 전혀 반영되지 않아야 한다는 것
    - 일관성 (Consistency)
        - 트랜잭션의 작업 처리 결과가 항상 일관성이 있어야 한다는 것
    - 격리성 (Isolation)
        - 어떤 하나의 트랜잭션이라도, 다른 트랜잭션의 연산에 끼어들 수 없다는 점
        - concurrency control의 주된 목표(isolation level로 transaction 설정)
    - 영구성 (Durability)
        - 트랜잭션이 성공적으로 완료됬을 경우, 결과는 영구적으로 반영되어야 한다는 점

### 연산

- Commit
    - 모든 작업을 정상처리하는 명령어
    - 한 개의 논리적 단위(트랜잭션)에 대한 작업이 성공적으로 끝나, 데이터베이스가 일관성 있는 상태를 의미
- Rollback
    - 작업 중 문제가 발생해, 트랜잭션의 처리과정에서 발생한 변경사항을 취소하는 명령어
    - 트랜잭션의 원자성이 깨져, 하나의 트랜잭션 처리가 비정상적으로 종료되었을 때의 상태를 의미

### 상태

![image.png](/img/Transaction/1.png)

- 활동(Active)
    - 트랜잭션이 정상적으로 실행중인 상태
- 부분 완료(Partially Committed)
    - 트랜잭션의 마지막까지 실행되었지만, Commit 연산이 실행되기 직전의 상태
- 완료(Committed)
    - 트랜잭션이 성공이 종료되어 Commit 연산을 실행한 후의 상태
- 실패(Failed)
    - 트랜잭션 실행에 오류가 발생하여 중단된 상태
- 철회(Aborted)
    - 트랜잭션이 비정상적으로 종료되어 Rollback 연산을 수행한 상태

### 질의응답

<details>
   <summary> 트랜잭션이란? (👈 Click)</summary>
데이터베이스의 상태를 변경하는 논리적인 작업 단위
</details>

<details>
   <summary> ACID 특징 중 Isolation란? (👈 Click)</summary>
어떤 하나의 트랜잭션도 다른 트랜잭션의 결과에 영향받지 않고 독립적으로 수행되는 특징으로, 동시성 제어에서 가장 중요한 역할을 한다.
</details>
<br>

> 참고 자료
> 

[https://www.youtube.com/watch?v=sLJ8ypeHGlM&list=PLcXyemr8ZeoT-_8yBc_p_lVwRRqUaN8ET&index=49](https://www.youtube.com/watch?v=sLJ8ypeHGlM&list=PLcXyemr8ZeoT-_8yBc_p_lVwRRqUaN8ET&index=49)
<br>
[https://inpa.tistory.com/entry/MYSQL-📚-트랜잭션Transaction-이란-💯-정리](https://inpa.tistory.com/entry/MYSQL-%F0%9F%93%9A-%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98Transaction-%EC%9D%B4%EB%9E%80-%F0%9F%92%AF-%EC%A0%95%EB%A6%AC)
<br>
[https://dev-coco.tistory.com/72](https://dev-coco.tistory.com/72)