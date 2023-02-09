# JSX

facebook에서 22년 8월4일에 낸 JSX draft

{% embed url="https://facebook.github.io/jsx/" %}

> JSX is an XML-like syntax extension to ECMAScript without any defined semantics.



> JSX는 XML처럼 작성된 부분을 React.createElement을 쓰는 JavaScript 코드로 변환한다. 중괄호를 써서 JavaScript 코드를 그대로 쓸 수 있고, 결국은 JavaScript 코드와 1:1로 매칭된다.

"JS 코드와 1:1로 매칭된다"

JSX 역시도 TS와 같이 JS 코드와 1:1로 매칭된다는 점

\=> 내 생각에 JSX(React)를 깊이 이해하는데 핵심이 되는 마음가짐이라는 생각.



변환기 중 제일 유명한 [Babel](https://babeljs.io/repl)로 확인 가능.

<mark style="background-color:orange;">=> Babel은 각 브라우저별로 다른 환경 및 버전 등을 해결해주는 변환기라고 생각했는데 더 다양한 기능들이 있는듯. 근데 최근 Babel을 직접 컨트롤한다거나 그런 내용은 못보긴 함</mark>

{% hint style="info" %}
해당링크에서   "Presets”에서 “react”를 체크하거나, “Plugins”에서 “@babel/plugin-transform-react-jsx”를 추가하면 JSX를 실험할 수 있다.
{% endhint %}



JSX 파일에 /\* @jsx 어쩌고 \*/ 주석을 추가하면 React.createElement 대신 “어쩌고”를 쓰게 된다.

#### Example #1

JSX 코드

```jsx
<p>Hello, world!</p>
```

변환된 JS 코드

```jsx
React.createElement("p", null, "Hello, world!");
```

\=> null은 이따 또 보고



<figure><img src="../../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

\=> props가 name="world"라고 내려주면 자동으로 {  name: "world" } 로 변환이 되는군, 이 이유는 아마도 React.createElement의 두번째 인자가 요구하는 형식이여서일꺼야.



여기에 추가로 요새 JSX

<figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

위에서 알아봤던 React.createElement 함수의 인자 세번째 자리(자식컴포넌트)에 아무것도 들어가지 않았다.

\=> 대신 두번째 인자(props)에 children이라는 속성이 추가되어 props 로 내려준다

\=> 실제로 과제 면접할 때 봤던 컴포넌트 props 형식이며 요즘은 이렇게 많이 사용.



<figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

\=> 위 내용을 보면 \<p> 태그의 변환 부분에 보면 "Count: ", count, "!" 를 볼 수 있다.&#x20;

\=> 태그 안에 텍스트는 string으로 처리가 된 반면에 {} 중괄호로 JSX에서 변수를 넣는 부분은 count 변수로 output이 되었다.

\=> 그리고 재밌는건 세번째 인자에 Count: {count}! 가 모두 들어가 있는게 아니라 모두 들어간다면 "Count:" + count + "!" 처럼 됐겠지????

\=> "Count:", count, "!" 로 마치 \<text>Count:\</text> 로 자식 태그로 들어간 것처럼 output이 만들어진다.



### React Element

* [JSX 없이 사용하는 React](https://ko.reactjs.org/docs/react-without-jsx.html)

쉽게일말해일히 React.createElement 하면 됨;;

* [createElement](https://beta.reactjs.org/reference/react/createElement)

JSX 대신 그냥 React.createElement를 써서 React Element 트리를 갱신하는데 쓸 수 있다.

JSX Runtime은 \_jsx란 함수를, Preact는 h란 함수를 직접 지원:

* [\_jsx](https://reactjs.org/blog/2020/09/22/introducing-the-new-jsx-transform.html)
* [h()](https://preactjs.com/guide/v10/api-reference/#h--createelement)

<mark style="background-color:orange;">=> 강의 중간에 내용이 나오긴 하는데 좀더 자세히 공부해보자 특히 "\_jsx"</mark>

###

### VDOM (Virtual DOM)

내 기존생각: 가상돔에 대한 이야기는 알고는 있다. 효율을 위해 리액트가 실제 돔을 건드리지 않고 가상 돔을 만들어 변화되는 부분들을 바꿔 보여주는 것을 말함.



상식적으로   생각해도 우리가 브라우저의 DOM을 변경해줄때 \
부분이변경이 될때마다 모든 곳을 렌더링할 필요 없다.

그러나 위에서 예시로 살펴봤던 JSX 코드들은

```javascript
React.createElement(
	"div",
	{ className: "test" },
	React.createElement("p", null, "Hello, world!"),
	React.createElement(Button, { type: "submit" }, "Send")
);
```

선택적으로 뭔가를수정 업데이트 내용이 없다.

그냥 다시 element를 만들 뿐이다.



아하 아! 사실 가상 돔이 어떤 효율을 위해 사용이 되는지 정확히는 몰랐다. 왜냐하면 가상 돔을  만든다는것은   어쨋건  VDOM 트리를 하나 더만든다는건 새로운 변경사항이 있을때 비교 분석 하는건 가상 돔 없이도 똑같이 해야하는 것이기 때문이다.



그런데. 만약 DOM 트리를 파싱을 해서 태그를 분석하고 자식의 자식의 끝의 모든 Node들까지 계속해서 분석해서 그 내부의 하나를 변경해주는 건 확실히 로직상 비효율 적이다. (마치 코테  알고리즘  문제에서 태그들을 분석해서 stack queue를 하듯) 어디에 있는것을 어떻게 바꿔라라고 정확히 명령을 내리기도 쉽지 않을 뿐더러 계속해서 해당 함수들이 돌아가야한다는 것이다.



반면에 가상 DOM 트리를 이용하면  React.createElement가새심플하게  계속 처음부터 끝까지 최신  정보에따라 렌더링해주고 이것을 이전 것과 1대1로 비교하면서 차이점을 단순 비교하면 복잡한 로직도 없고 단순 비교를 하면 됨으로 훨씬 효율적이고 직관적이고 심플해진다.



<mark style="background-color:orange;">=> 근데 사실 이건 추측... 한번 조사를 통해 확신을 가질 수 있도록 하자</mark>&#x20;



### VDOM을 쓰는 이유?

미신 : VDOM을 쓰는 건 빠르기 때문?

🤪  [현실](https://twitter.com/dan\_abramov/status/842329893044146176)&#x20;

→ fast enough  (빠르긴 함)

→ maintainable (유지보수)

&#x20; 선언형 UI라는 좋은 구조를 줌

&#x20; jquery 보다 뭐가 특별하게 다르고 그런게 아님.

Dan Abramov

* [Redux](https://redux.js.org/) 창시자
* [React Core 개발자](https://beta.reactjs.org/learn/meet-the-team)



### 그래서 VDOM은 무엇인가요?

{% embed url="https://ko.reactjs.org/docs/faq-internals.html" %}

그래서 VDOM !== DOM &#x20;

예를 들어, VDOM에 있는 \<Fragment> 같은건 DOM에 없음







{% hint style="info" %}
### React Developer Tools

*   [react devtools extensions](https://github.com/facebook/react/tree/main/packages/react-devtools-extensions)

    → [Strict Mode](https://ko.reactjs.org/docs/strict-mode.html)를 쓰지 않으면 경고함.
* profiler는 성능 향상 할때 주로 사용

![](../../.gitbook/assets/image.png)
{% endhint %}



{% hint style="info" %}
JS Strict Mode 와 React Strict Mode가 조금 다르다. React Strict Mode 기능의 대표적인 예시로 렌더링을 두번 해주는데 이 두번의 렌더링에서 뭐가 다른게 있으면 side effect 가 있다고 에러 내주기도 한다.
{% endhint %}

```jsx
root.render(
  <React.StrictMode>
    <QueryClientProvider client={queryClient}>
      <RecoilRoot>
        <BrowserRouter>
          <App />
        </BrowserRouter>
      </RecoilRoot>
    </QueryClientProvider>
  </React.StrictMode>
);
```

\=> 실제로 react에서 기본으로생기는 index.js에는 React.StrictMode가 존재.













