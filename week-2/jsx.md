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



<figure><img src="../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

\=> props가 name="world"라고 내려주면 자동으로 {  name: "world" } 로 변환이 되는군, 이 이유는 아마도 React.createElement의 두번째 인자가 요구하는 형식이여서일꺼야.



여기에 추가로 요새 JSX

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

위에서 알아봤던 React.createElement 함수의 인자 세번째 자리(자식컴포넌트)에 아무것도 들어가지 않았다.

\=> 대신 두번째 인자(props)에 children이라는 속성이 추가되어 props 로 내려준다

\=> 실제로 과제 면접할 때 봤던 컴포넌트 props 형식이며 요즘은 이렇게 많이 사용.



<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

\=> 위 내용을 보면 \<p> 태그의 변환 부분에 보면 "Count: ", count, "!" 를 볼 수 있다.&#x20;

\=> 태그 안에 텍스트는 string으로 처리가 된 반면에 {} 중괄호로 JSX에서 변수를 넣는 부분은 count 변수로 output이 되었다.

\=> 그리고 재밌는건 세번째 인자에 Count: {count}! 가 모두 들어가 있는게 아니라 모두 들어간다면 "Count:" + count + "!" 처럼 됐겠지????

\=> "Count:", count, "!" 로 마치 \<text>Count:\</text> 로 자식 태그로 들어간 것처럼 output이 만들어진다.



35:48





