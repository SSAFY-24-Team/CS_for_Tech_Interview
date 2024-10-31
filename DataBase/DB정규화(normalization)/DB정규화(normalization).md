# DB정규화(normalization)

# 함수 종속(functional dependency)

![image.png](/img/DB_normalization/0.png)

- X값이 같다면 Y값도 같다.
- X값에 따라 Y값이 유일하게 결정될 때, X가 Y를 함수적으로 결정한다 (X→Y)
- 테이블의 스키마를 보고 의미적으로 FD가 존재하는지 파악
- X→Y not means Y→X
- {} → Y
    - Y값은 언제나 동일한 값
- trivial FD
    - X→Y일 때 Y가 X의 부분집합일 경우
- Non-trivial FD
    - X→Y일 때 Y가 X의 부분집합이 아닌 경우
- Partial functional dependency
    - X→Y이고 X의 proper subset이 Y를 결정할 때
    - proper subset: 부분집합이지만 완전 동일하지 않은경우
        - e.g. X={a,b,c}, X의 proper subset={a,c}, {a,}, {}
- Full functional dependency
    - X→Y이고 X의 모든 proper subset이 Y를 결정지을 수 없을때

# **이상현상(Anomly)**

- 테이블을 설계할 때 잘못 설계하여 데이터를 삽입, 삭제, 수정할 때 논리적으로 생기는 오류
    - 삭제 이상: 튜플 삭제 시 같이 저장된 다른 정보까지 연쇄적으로 삭제되는 현상
    - 삽입 이상: 튜플 삽입 시 특정 속성에 해당하는 값이 없어 NULL을 입력해야 하는 현상
    - 수정 이상: 튜플 수정 시 중복된 데이터의 일부만 수정되어 일어나는 데이터 불일치 현상

# 정규화란?

- 데이터 중복, 이상 현상을 최소화하기 위해 normal form(NF)에 따라 relation을 구성하는 것
- 앞 단계를 만족해야 다음 단계로 진행할 수 있다. 즉, 현재 단계 이전의 정규화는 다 만족하고 있다.
- BCNF까지는 functional dependency와 key만으로 정의된다.

# 종류

### 1NF

- 테이블의 컬럼이 원자값(Atomic Value, 하나의 값)을 갖도록 테이블을 분해하는 것
- 중복 데이터가 생기고 primary key도 변경해야할 수 있다.

![image.png](/img/DB_normalization/1.png)

### 2NF

- 제1 정규형을 만족하고, 기본키가 아닌 속성이 기본키에 완전 함수 종속
- key가 composite key가 아니라면 2NF는 자동적으로 만족한다?
    - {}→Y인 경우의 예외를 생각해야한다. 하지만, 대체로 만족한다.

![image.png](/img/DB_normalization/2.png)

![image.png](/img/DB_normalization/3.png)

### 3NF

- 릴레이션 R이 제2 정규형을 만족하고 기본키가 아닌 속성이 기본키에 비이행적(Non-Transitive)으로 종속할 때(직접 종속)
    - 모든 non-prime attribute는 어떤 Key에도 transitively dependent하면 안된다.
- non-prime attribute와 non-prime attribute 사이에는 functional dependency가 있으면 안된다.
- X→Y & Y→Z 이면 X→Z이다. transitive functional dependency, Y나 Z는 어떤 key의 부분 집합이 아니여야함

![image.png](/img/DB_normalization/4.png)

### BCNF

- 릴레이션 R에서 함수 종속성 X->Y가 성립할 때 모든 결정자 X가 후보키인 정규형
    - 모든 유효한 non-trivial functional dependency X→Y는 X가 super key여야 한다.

![image.png](/img/DB_normalization/5.png)

![image.png](/img/DB_normalization/6.png)

### 질의응답

<details>
   <summary> DB 정규화란? (👈 Click)</summary>
데이터의 중복을 제거해, 이상현상을 방지하고 무결성을 유지하는 기법

</details>
<br>

> 참고자료
>
[https://www.youtube.com/watch?v=fw8hvolebLw&list=PLcXyemr8ZeoREWGhhZi5FZs6cvymjIBVe&index=22](https://www.youtube.com/watch?v=fw8hvolebLw&list=PLcXyemr8ZeoREWGhhZi5FZs6cvymjIBVe&index=22)
<br>
[https://www.youtube.com/watch?v=EdkjkifH-m8&list=PLcXyemr8ZeoREWGhhZi5FZs6cvymjIBVe&index=23](https://www.youtube.com/watch?v=EdkjkifH-m8&list=PLcXyemr8ZeoREWGhhZi5FZs6cvymjIBVe&index=23)
<br>
[https://www.youtube.com/watch?v=5QhkZkrqFL4&list=PLcXyemr8ZeoREWGhhZi5FZs6cvymjIBVe&index=24](https://www.youtube.com/watch?v=5QhkZkrqFL4&list=PLcXyemr8ZeoREWGhhZi5FZs6cvymjIBVe&index=24)
<br>
[https://mangkyu.tistory.com/28](https://mangkyu.tistory.com/28)
<br>
[https://dev-coco.tistory.com/63](https://dev-coco.tistory.com/63)