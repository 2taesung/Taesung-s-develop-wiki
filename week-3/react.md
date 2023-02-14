# React

### React의 강력한 특징 둘&#x20;

> #### Declarative

F/E는 데이터를 사용자가 볼 수 있도록 UI를 구성한다. React는 선언형(HTML과 유사한 모양의 DSL을 사용)으로 UI를 구성할 수 있다.

<mark style="background-color:green;">=> DSL (domain specific language) 솔직히 찾아봤는데 무엇인지 이해하기 어려움</mark>

[아샬님의 dsl 설명 영상](https://youtu.be/2zW4dls8\_sw)

\=> 이해함. 어떤 특정 목표를 가지고 있는 언어를 표현하는 것.&#x20;

\=> 예를들면, html 은 웹에 화면을 보여주는 dsl인 셈.

\=> 고로 React의 선언형도 웹에 데이터를 잘 보여주는 dsl인것이다.



원래는 FE  개발에서데이터들을 append하고 자시고 해야하는데 &#x20;

(JS만 생각해봐도 select 하고  node에서 append하고 .... 등)



그런데  우리의 React는 '선언형 UI'라고 표현된다.

'선언형'이란 데이터를 어떻게 활용할지(보여줄지) 명령 내려놓으면,

그리고데이터가 변하면  선언한 상태 그대로 자동으로 반영해보여주는 것이다.



두번째,

> #### Component-Based

Build <mark style="background-color:purple;">encapsulated components</mark> that manage their own state, then compose them to make <mark style="background-color:purple;">complex UIs</mark>.

\=> 컴포넌트는 어려운게 아니다.&#x20;

\=> <mark style="background-color:purple;">간단한 컴포넌트를 가지고 복잡한 UI를 만드는게</mark> 포인트

\=> 만약 복잡한 컴포넌트를 만들고 있다면 React의 장점을 잘 활용하지 못하고 있는 것.



그렇다면 '간단한 컴포넌트'의 '간단한'의 기준이 뭐냐.

