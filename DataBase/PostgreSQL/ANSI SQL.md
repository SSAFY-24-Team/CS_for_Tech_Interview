![img.png](img/ANSI%20SQL/img.png)

# 🖐 ANSI SQL

    MySQL이나 PostgreSQL 등 DB와 SQL을 공부하다 보면 'ANSI SQL'이라는 단어를 접하게 된다.
    이 단어의 뜻과 오해를 알아보자.

## ❓ ANSI

- ANSI란 미국 국가 표준 협회 (ANSI : American National Standards Institute)이다.
- 위 사진은 ANSI 블로그이며 주소는 다음과 같다. (https://blog.ansi.org/)
- ANSI의 역할은 다음과 같다.
    - 미국에서 표준화 활동을 조정하고 관리하는 비영리 기구
    - 자발적으로 미국 제품, 프로세스, 시스템 등을 위한 표준 제정 담당
    - 미국 제품이 세계에서 통용되기 위해 국제적인 기준에 부합하는 기준을 제정
    - ANSI가 제정한 표준 중 가장 유명한 것이 ASCII 코드(아스키코드)이다.
- 국제표준화기구 ISO(International Organization for Standardization)에 가입되어 있다.

## 💡 ANSI SQL

![img_1.png](img/ANSI%20SQL/img_1.png)

- SQL 표준에 대해서 설명한 ANSI 블로그의 포스팅 글을 살펴보자.
- 흔히들 'ANSI SQL 표준을 따랐다~' 라고 표현하기도 하는데, 이에대한 ANSI 블로그의 설명부분을 보면 '오해'라고 한다.
- 해당 포스팅의 주소 : https://blog.ansi.org/sql-standard-iso-iec-9075-2023-ansi-x3-135/

<br/>

![img_2.png](img/ANSI%20SQL/img_2.png)

- 놀랍게도 그러한 표준은 없다고한다...왜냐하면 ANSI는 표준 자체를 개발하지 않고, 표준 개발을 지원하거나 조정하는 역할이기 때문이라고 한다.
- 역사를 살펴보면 1986년 SQL언어가 공식적으로 수용되었고, 공인 표준 위원회(ASC) X3의 ANSI 데이터베이서 기술 의원회(ANSI X3H2)가 최초로 SQL 표준을 개발했다고 한다.
- 해당 문서는 'ANSI X3.135-1986'이며 이것을 사람들이 ANSI 표준이라고 부르게 되며 오해가 생겼다고 한다.
- ANSI 표준이 아니라, ANSI 승인 위원회에서 개발한 표준이고, 몇 달 이후 정식 국제 표준으로 ISO의 'ISO 9075'로 대체되었다고 한다.

## IOS 9075

![img_3.png](img/ANSI%20SQL/img_3.png)

- 데이터베이스 언어인 SQL의 IOS 표준 문서이다.
- 치사하게 PDF가 유료인데, 쌤플 정보를 볼 수도 있는 것 같다.
- 주소 : https://www.iso.org/standard/76583.html

<br/>

![img_4.png](img/ANSI%20SQL/img_4.png)

## ✔ 정리

- 정리하면 ANSI SQL 표준이라는 것은 없고, 정리 문서에서 비롯한 오해였다.
- 하지만 SQL 세계 표준인 'ISO 9075'가 만들어지는데 참고가 된 원조 격의 문서라고 볼 수 있다.

  
---  

## 예제 질문

#### ANSI SQL 표준이란?

<details>
   <summary> 예비 답안 보기 (👈 Click)</summary>
<br />

ANSI SQL 표준은 실제로 존재하지 않으며, 이는 오해에서 비롯된 표현입니다. ANSI는 미국 국가 표준 협회로서 표준을 직접 개발하지 않고, 표준 개발을 지원하거나 조정하는 역할을 합니다. 1986년 ANSI의 데이터베이스 기술 위원회(ANSI X3H2)가 최초로 SQL 표준을 개발했지만, 몇 달 후 ISO가 이를 국제 표준(ISO 9075)으로 대체했습니다. 따라서, ANSI SQL이라는 용어는 ISO 9075 표준에 대한 초기 문서에서 비롯된 잘못된 명칭입니다.

</details>

### ANSI와 ISO의 차이점은 무엇인가요?

<details>
   <summary> 예비 답안 보기 (👈 Click)</summary>
<br />

ANSI는 미국 국가 표준 협회로, 미국 내 표준을 조정하고 관리하는 역할을 하는 비영리 기구입니다. 반면, ISO(국제 표준화 기구)는 전 세계적으로 통용되는 국제 표준을 개발하는 기구입니다. ANSI는 ISO의 미국 대표 기관으로, ANSI에서 개발한 일부 표준이 ISO 표준으로 이어지기도 합니다.

</details>

### SQL 표준은 누가 개발하고 관리하나요?

<details>
   <summary> 예비 답안 보기 (👈 Click)</summary>
<br />

SQL 표준은 국제적으로 ISO(International Organization for Standardization)와 IEC(International Electrotechnical Commission)가 공동으로 개발하고 관리합니다. 현재 SQL 표준은 ISO/IEC 9075라는 이름으로 관리되며, 이 표준은 데이터베이스 관리 시스템에서 SQL을 사용하는 데 필요한 규격을 정의하고 있습니다.

</details>

### ANSI가 처음 SQL 표준을 만들었다는 오해가 생긴 이유는?

<details>
   <summary> 예비 답안 보기 (👈 Click)</summary>
<br />

1986년에 ANSI의 데이터베이스 기술 위원회가 SQL 표준을 개발한 후, 이 문서가 'ANSI X3.135-1986'이라는 이름으로 불리면서 사람들이 이를 ANSI SQL 표준이라고 부르기 시작했습니다. 하지만 ANSI는 실제로 표준을 개발하는 기관이 아니며, 이 표준은 곧 ISO의 'ISO 9075'로 대체되었습니다. 그래서 ANSI SQL이라는 용어는 오해에서 비롯된 잘못된 표현입니다.

</details>

