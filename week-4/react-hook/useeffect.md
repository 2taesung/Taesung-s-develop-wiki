# useEffect

[https://beta.reactjs.org/learn/synchronizing-with-effects](https://beta.reactjs.org/learn/synchronizing-with-effects)

> Some components need to synchronize with external systems.

synchronize라 함은 컴포넌트 외부에서 영향을 받는 것을 뜻 해.

예를 들면 props의 변화, axios를 통해 외부에서 들어오는 데이터.



되도록이면 useEffect를 쓰지마라(useEffect를 쓰는 상황을 강조하려함)

[You Might Not Need an Effect](https://beta.reactjs.org/learn/you-might-not-need-an-effect)

내가 생각했을때도 이름이 sideEffect 처럼 부작용의 의미도 useEffect에는 포함되어 있다.

왜냐하면 함수형 프로그래밍, 함수 단위의 유닛테스트 생각했을 때 함수의 input과 output에 집중을 하니까 return (output)으로 의미 있는 가치를 만들지 않는 useEffect 같은 경우는 함수형 프로그래밍의 철학에 어긋나는 셈이니까.



> 렌더링 이후 해야 할 일, 즉 React의 외부와 관련된 일을 정해줄 수 있다.
>
> 기본적으로 두번째 인자로 타이밍을 잡아주지 않는다면 렌더링시 항상 실행된다.
>
> 렌더링시에는 당연 state가 변경될때도 포함한다.

<mark style="background-color:orange;">예를 들어, DOM으로 떨어졌을때 그것을 잡기 위해 사용하기도 함 ???</mark>



```javascript
useEffect(() => {
    document.title = `Now: ${new Date().getTime()}`;
});
```

\=> 렌더링 시 항상 작동. state가 바뀔때도 실행이 됨으로&#x20;

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

\=> 위의 검색의 내용을 바꾸더라도(state 변경) 제목의 값이 변경된다.

\=> 내가 진짜 지금까지 useEffect를 잘못 사용하고 있었음...

\=> 나의 useEffect 의 사용 방법은 그냥 데이터가 새로 파생될때 항상 사용했다.

\=> 물론, return (clean up)도 제대로 하지 않았고.

\=> 그러니 말 그대로 side Effect rendering들이 다수 발생할 수 밖에 없었지...















