# 트랜잭션 격리성

# 트랜잭션들이 동시에 실행될 때 발생 가능한 이상 현상

### Dirty Read

- 다른 트랜잭션에 의해 수정되었지만 아직 커밋되지 않은 상태의 데이터를 읽는 현상
    
    ![image.png](/img/Isolation/0.png)
    
    - 트랜잭션1이 롤백된다면, 트랜잭션2에서 data2를 사용할 경우 문제가 발생할 수 있다.

### Non-Repeatable Read

- 하나의 트랜잭션에서 같은 데이터를 반복적으로 읽을때, 결과가 다르게 나타나는 현상
    
    ![image.png](/img/Isolation/1.png)
    
    - 트랜잭션1이 진행 중인 상태에서 트랜잭션2로 인해 key=2의 데이터가 변경되면, Select1와 Select2의 key=2의 데이터가 달라지게 된다.

### Phantom Read

- 첫 번째 쿼리 결과에 없는 유령(Phantom) 데이터가 두 번째 쿼리 결과에 나타나는 현상
- Non-Repeatable Read와 유사하지만, 여러 개의 데이터를 조회할 때 발생한다는 점이 다르다
    
    ![image.png](/img/Isolation/2.png)
    
    - 트랜잭션1이 진행 중인 상태에서 트랜잭션2로 인해 key=3의 data3이 삽입될 경우, Select1에서는 조회되지 않던 data3이 조회된다.

# 트랜잭션 격리 수준

- 여러 트랜잭션이 동시에 처리될 때, 특정 트랜잭션이 다른 트랜잭션에서 변경하거나 조회하는 데이터를 볼 수 있게 허용할지 여부를 결정
- 격리 수준에 따라 발생할 수 있는 이상 현상도 다르다.
- 동시성과 일관성은 반비례 관계를 갖는다.

![image.png](/img/Isolation/3.png)

### Serializable

- 트랜잭션을 순차적으로 진행하는 격리 수준
- 여러 트랜잭션이 동일한 레코드에 동시 접근 할 수 없어, 데이터 부정합 문제가 발생하지 않는다.
- 가장 안전하지만, 동시성이 매우 떨어진다는 단점을 갖는다.

### Repeatable Read

- 한 트랜잭션 내에서 동일한 결과를 보장하는 격리 수준
- 실제 데이터가 아닌 Undo 로그에 있는 백업데이터를 읽는다.
- 새로운 레코드가 추가되는 경우 부정합이 발생할 수 있다.

### Read Committed

- 커밋이 확정된 데이터만 조회하는 격리 수준

### Read Uncommitted

- 커밋되지 않은 데이터도 접근할 수 있는 격리 수준
- 정합성에 많은 문제가 발생한다.

|  | Dirty Read | Non-Repeatable Read | Phantom Read |
| --- | --- | --- | --- |
| Read Uncommited | O | O | O |
| Read Committed | X | O | O |
| Repeatable Read | X | X | O |
| Serializable | X | X | X |

### 질의응답

<details>
   <summary> 트랜잭션 격리 레벨 중 가장 안전한 레벨은 무엇이고 단점은? (👈 Click)</summary>
Serializable이며, 동시성이 매우 떨어진다는 단점으로 DBMS에서 거의 사용하지 않는다.

</details>
<br>

> 참고자료
> 

[https://innovation123.tistory.com/166](https://innovation123.tistory.com/166)
<br>
[https://mangkyu.tistory.com/299](https://mangkyu.tistory.com/299)
<br>
[https://sabarada.tistory.com/117](https://sabarada.tistory.com/117)