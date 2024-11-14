## 🌀 props

> 부모 컴포넌트가 자식 컴포넌트에 전달하는 데이터 (컴포넌트 간 데이터 전달)
> 읽기 전용으로, 자식 컴포넌트는 props를 수정할 수 없음

모든 React 컴포넌트는 자신의 props를 다룰 때 반드시 순수 함수처럼 동작해야 한다.

> **순수함수**
> 입력값을 바꾸지않고 항상 동일한 입력값에 대해 동일한 결과를 반환하는 함수

props는 컴포넌트 간의 **데이터 흐름을 예측 가능하게** 만들고, 컴포넌트의 **재사용성을 높임**

### 🫧 props가 자식 컴포넌트에서 변하지 않는 이유

리액트의 **단방향 데이터 흐름 원칙** 때문.
리액트는 부모 컴포넌트가 자식 컴포넌트에 데이터를 전달할 때 단방향으로 전달하도록 설계되어있음. 이렇게 하면 컴포넌트 간의 데이터 흐름을 예측 가능하고 일관성 있게 만들 수 있어 애플리케이션 상태 관리가 간단해짐

props는 읽기 전용이기 때문에, 부모 컴토넌트에서 전달된 값이 자식 컴포넌트 내에서 임의로 변경되지않음.
이로 인해, 특정 상태가 어디서 어떻게 변했는지를 예측할 수 있어 버그 발생 가능성을 줄이고 디버깅을 쉽게 할 수 있음

만약 props가 변경될 수 있다면, 자식 컴포넌트는 독립적으로 동작하지 않게 되고, 재사용이 어려워질 수 있음. props가 불변으로 유지됨으로써 컴포넌트는 외부입력에 의존할 뿐 내부적으로 변경하지 않아 재사용성이 높아지고, 코드의 캡슐화가 강화됨

### 🫧 만약 자식 컴포넌트에서 props를 변경해야한다면?

상태를 부모 컴포넌트로 올려 부모 컴포넌트에서 props를 다시 전달하는 방식으로 구현해야함.
이렇게 하면 데이터는 여전히 단방향으로 흐르고, 상태는 부모 컴포넌트가 관리해 일관성을 유지할 수 있음.
이러한 기법을 상태 끌어올리기라고 함

### 🫧 props와 state

두 가지 모두 컴포넌트 기반 애플리케이션에서 데이터를 관리하는 데 필수적이지만 서로 다른 목적을 가짐.

#### props

데이터를 부모로부터 자식 컴포넌트로 전달하는 데 사용되며 단방향 데이터 흐름을 설정.
부모에 의해 설정되며 자식 컴포넌트에 의해 변경 불가

#### state

컴포넌트 내부의 것으로 동작과 렌더링을 제어
props와 달리 상태는 가변적이며 보통 사용자의 행동이나 시스템 이벤트에 응답하여 시간이 자남에 따라 변할 수 있음

### 출처

[매일메일-리액트의 props와 state에 대해서 설명해주세요](https://www.maeil-mail.kr/question/16)
[리액트 공식문서](https://ko.legacy.reactjs.org/docs/components-and-props.html)