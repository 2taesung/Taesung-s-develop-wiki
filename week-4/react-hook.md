# React의 Hook

기존 방식의 문제점:

* Wrapper Hell (HoC)

\=> 고차함수의 특징을 이용하여 함수 안에 함수를 넣는 (wrapper) 등의 행위로 인해 복잡한 코드 상황 발생

* Huge Components
* Confusing Classes

\=> class를 사용하면 사용 안할 수 있는 this 등 때문에 코드가 어려워짐.

기존:

* 상태를 가진 컴포넌트는 Class Component로 만들고, props만 사용하는 재사용이 용이한 작은 컴포넌트는 Function Component로 작성.
* Redux에서도 비슷한 구분이 존재했다.
  * [Presentational and Container Components - Dan Abramov](https://medium.com/@dan\_abramov/smart-and-dumb-components-7ca2f9a7c7d0)

\=> 디자인 패턴 중에서도 해당 내용이 있음. 그러나 요즘엔 이런 디자인 패턴은 사용하지 않음.

[presentational & container 디자인 패턴](https://kyounghwan01.github.io/blog/React/container-presenter-dessign-pattern/)\


현재:

* 그냥 Function Component만 사용.
* 상태 관리 유무를 바로 알기 어려움 = 신경쓰지 않아도 됨.&#x20;

&#x20;    (예전에는 class 를 쓰면 상태관리를 한다라는 거였다)

* 복잡한 요소는 전부 Hook으로 격리 및 재사용 가능.

&#x20;    (useCustom으로 복잡한 로직의 격리 및 재사용이 가능해짐)



대표적인 Hooks

\=> Hooks는 React를 이루는 도구일 뿐이다.

* useState → State Hook ⇒ React의 State
* useEffect ⇒ Side-effect
* useContext
* useRef
* useLayoutEffect → useEffect와 조금 다름.
