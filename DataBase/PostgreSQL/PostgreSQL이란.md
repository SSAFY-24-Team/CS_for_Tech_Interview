![img.png](img/PostgreSQL이란%20이미지/img.png)
# 🐘 PostgreSQL이란?
    귀여운 코끼리 로고로 유명한 PostgreSQL에 대해 알아보자.
    정의, 배경, 사용 이유, MySQL과의 차이 등을 서술한다.


## 🚀 정의 / 배경
![img.png](img/PostgreSQL이란%20이미지/img2.png)

PostgreSQL의 공식 사이트 (https://www.postgresql.org/)는 이렇게 소개하고 있다.

> PostgreSQL: 세계에서 가장 진보된 오픈소스 관계형 데이터베이스

관계형 데이터베이스(RDBMS) 중 대표되는 PostgreSQL은 무려 오픈소스로 제공되고 있다.  
전 세계 커뮤니티에서 개발 과 유지보수가 이루어지고, 그 성능이 뛰어나 점차 영향력이 커져가는 DBMS이다. 

공식 사이트에서는 **간략한 역사**도 설명해주고 있다. 원문은 [링크](https://www.postgresql.org/docs/current/history.html)를 확인하고 GPT의 요약은 다음과 같다.  
![img_1.png](img/PostgreSQL이란%20이미지/img_1.png)
> PostgreSQL는 캘리포니아 대학교 버클리에서 시작된 POSTGRES 프로젝트에서 유래한 객체-관계형 데이터베이스 관리 시스템입니다. 1986년 Michael Stonebraker 교수가 이끈 이 프로젝트는 DARPA, ARO, NSF 등의 후원을 받아 개발되었습니다. 초기 버전은 1989년에 외부 사용자에게 공개되었으며, 이후 여러 연구 및 상용 애플리케이션에서 사용되었습니다. 1994년 Andrew Yu와 Jolly Chen이 SQL 인터프리터를 추가해 Postgres95라는 이름으로 공개되었고, 성능과 유지 관리가 개선되었습니다. 1996년에는 SQL 기능을 반영하기 위해 이름을 PostgreSQL로 변경했고, 이후로도 기능 확장과 개선 작업이 계속되고 있습니다.


여기서 단순히 관계형 데이터베이스가 아닌, '객체-관계형 데이터베이스'라고 불리는 이유는 다음과 같은 객체 지향적인 특성을 포함시켰기 때문이다.
 1. 사용자 정의 타입
 2. 상속
 3. 메서드 및 함수
 4. 다형성
 5. 복합 데이터 타입

심지어 NoSQL의 기능도 일부 지원하며, 다양한 데이터 관리 요구에 유연하게 대응할 수 있는 하이브리드 데이터베이스이다.
(사실 NoSQL이 RDBMS를 포함한 개념이긴 하다...)


## ❓ 사용 이유
그렇다면 PostgreSQL은 왜 사용할까? 강점은 무엇일까?
<br>

![img_2.png](img/PostgreSQL이란%20이미지/img_2.png)  
[네이버 D2 포스팅 : 한눈에 살펴보는 PostgreSQL(2012.12.15)](https://d2.naver.com/helloworld/227936)  
12년도 당시는 새롭게 인기를 끌어가며, 오픈 소스라는 장점으로 오라클 사용자들을 흡수해 나간 것 같다.
역시 무료가 플랫폼 장악에서 중요하다.  

<br>

![img_3.png](img/PostgreSQL이란%20이미지/img_3.png)  
[IBM 기술 블로그 : PostgreSQL이란 무엇입니까?](https://www.ibm.com/kr-ko/topics/postgresql)  
IBM은 PostgreSQL의 장점을 다음과 같이 정의했다.
- 뛰어난 **안정성**과 **유연성**, **개방형 기술 표준** 지원
- **동적 데이터베이스 시스템** 유지 유지 용이
- 확장 가능, 시계열 데이터부터 광범위한 확장 에코 시스템 등으로 **특수 사용 사례를 신속하게 지원**
- 뛰어난 성능 및 확장성
- 동시성 지원
- 심층적 언어 지원
- 비지니스 연속성
- 100% 오픈소스

정리하자면 강력하고, 다재능하며, 심지어 무료이다. 학생 개인이나 기업에서 안 쓸 이유가 없는 DBMS이다.  

아직 교과 과정에선 MySQL이 먼저로 보이지만, 기업에은 PostgreSQL을 선호하는 모습을 자주 보았다.  
(채용 공고에서 요구 기술로 많이 언급되고, AWS RDS의 DBMS 선택 순서도 PostgreSQL이 첫 번째로 바뀐 것 등)


## 🎆 MySQL과의 차이점
다양한 차이점이 있지만 간략하게 알아보자.
### 1. 데이터베이스 모델
   - **PostgreSQL**: 객체-관계형 데이터베이스 관리 시스템(ORDBMS). 관계형 데이터베이스의 특성과 더불어 객체 지향 기능을 지원하며, 다양한 확장성과 복잡한 데이터 타입을 처리할 수 있습니다.
   - **MySQL**: 전통적인 관계형 데이터베이스 관리 시스템(RDBMS). 간단하고 빠른 성능을 목표로 하며, 주로 스키마 기반 데이터 모델을 사용합니다.
### 2. ACID 및 트랜잭션 처리
   - **PostgreSQL**: PostgreSQL은 ACID(Atomicity, Consistency, Isolation, Durability)를 철저히 준수  
   - **MySQL**: MySQL은 InnoDB 스토리지 엔진을 사용할 때 ACID를 지원. 하지만 다른 스토리지 엔진을 사용할 경우 ACID를 완전히 보장하지 않으며, 트랜잭션 처리 기능이 제한될 수 있음.
### 3. 확장성 및 확장 기능
   - **PostgreSQL**: PostgreSQL은 다양한 확장성을 제공하며, 사용자 정의 함수, 데이터 타입, 인덱스 등을 쉽게 추가할 수 있습니다.
   - **MySQL**: MySQL은 간단한 확장 기능만 지원. 복잡한 확장성보다는 기본적인 데이터베이스 기능에 중점을 둡니다.
### 4. SQL 표준 준수
   - **PostgreSQL**: SQL 표준을 매우 엄격하게 준수하는 데이터베이스
   - **MySQL**: MySQL도 SQL 표준을 지원하지만, PostgreSQL만큼 완벽하지는 않음.
### 5. NoSQL 기능
   - **PostgreSQL**: PostgreSQL은 JSON 및 JSONB를 지원하여 NoSQL 방식의 비정형 데이터를 관리할 수 있음.
   - **MySQL**: MySQL도 JSON 데이터 타입을 지원하지만, PostgreSQL의 JSON 처리 능력에 비해 기능이 제한적.
### 6. 성능
   - **PostgreSQL**: PostgreSQL은 트랜잭션 처리, 동시성 제어, 복잡한 쿼리 최적화 등에서 강력한 성능을 제공. 고성능이 필요한 대규모 시스템에서 뛰어난 성능.
   - **MySQL**: MySQL은 주로 간단한 쿼리 처리와 읽기 위주의 애플리케이션에서 빠른 성능.

## 🖐 정리
- PostgreSQL은 복잡한 데이터 처리와 확장성이 필요한 애플리케이션에 적합
- SQL 표준 준수와 NoSQL 기능까지 제공하는 강력한 데이터베이스
- MySQL은 간단하고 빠른 처리 성능을 요구하는 애플리케이션, 특히 웹 애플리케이션에서 널리 사용

## 예제 질문
### 1. PostgreSQL이란? 왜 객체-관계형 데이터베이스로 불리나요?

<details>
   <summary> 예비 답안 보기 (👈 Click)</summary>
<br />

PostgreSQL은 객체 지향적인 특성을 추가하여, 사용자 정의 타입, 상속, 메서드 및 함수, 다형성, 복합 데이터 타입 등을 지원하는 객체-관계형 데이터베이스입니다. 이는 단순한 관계형 데이터베이스와는 차별화된 특징으로, 다양한 데이터 관리와 확장성을 제공합니다.

</details>

### 2. PostgreSQL과 MySQL의 차이점은?

<details>
   <summary> 예비 답안 보기 (👈 Click)</summary>
<br />

1. **데이터베이스 모델**
    - PostgreSQL은 객체-관계형 데이터베이스(ORDBMS)로, 사용자 정의 타입과 확장성을 제공하며 복잡한 데이터를 처리할 수 있습니다. 반면, MySQL은 전통적인 관계형 데이터베이스로, 빠른 성능을
      중점에 둔 간단한 데이터 모델을 지원합니다.
2. **NoSQL 기능**
    - PostgreSQL은 JSON 및 JSONB를 통해 NoSQL 기능도 지원하여 비정형 데이터를 효율적으로 관리할 수 있습니다. MySQL도 JSON 데이터를 지원하지만, PostgreSQL의 처리 성능에는
      미치지 못합니다.
3. **ACID 및 트랜잭션 처리**
    - PostgreSQL은 트랜잭션 처리와 ACID(원자성, 일관성, 고립성, 지속성)를 완벽히 준수합니다. MySQL은 InnoDB 엔진에서 ACID를 지원하지만, 다른 스토리지 엔진에서는 제한적일 수
      있습니다.
4. **ANSI SQL 표준 준수**
    - PostgreSQL은 **ANSI SQL**(국제 표준 SQL)을 철저히 준수하여 최신 SQL 기능을 광범위하게 지원합니다. 이로 인해 복잡한 쿼리 작성이 용이하고 이식성이 뛰어납니다. MySQL도 SQL
      표준을 지원하지만, PostgreSQL만큼 완벽하지 않으며 일부 기능은 제한적입니다.

</details>


