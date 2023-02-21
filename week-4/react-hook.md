# React의 Hook

기존 방식의 문제점:

* Wrapper Hell (HoC)
* Huge Components
* Confusing Classes

기존:

* 상태를 가진 컴포넌트는 Class Component로 만들고, props만 사용하는 재사용이 용이한 작은 컴포넌트는 Function Component로 작성.
* Redux에서도 비슷한 구분이 존재했다.
  * [Presentational and Container Components - Dan Abramov](https://medium.com/@dan\_abramov/smart-and-dumb-components-7ca2f9a7c7d0)

현재:

* 그냥 Function Component만 사용.
* 상태 관리 유무를 바로 알기 어려움 = 신경쓰지 않아도 됨.
* 복잡한 요소는 전부 Hook으로 격리 및 재사용 가능.



대표적인 Hooks

* useState → State Hook ⇒ React의 State
* useEffect ⇒ Side-effect
* useContext
* useRef
* useLayoutEffect → useEffect와 조금 다름.



### useEffect

외부와 sync 할 경우 쓴다.



