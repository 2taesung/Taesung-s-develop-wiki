# State

* “Step 3: Find the minimal but complete representation of UI state”
* “Step 4: Identify where your state should live”

useState로 대표되는 state 역시 React로 개발을 하는데 SRP와 양대산맥.

\=> 현재까지는 무지성으로 필요한 경우에 useState를 만들어썼다.

\=> 그러나 이제부터는 React 안의 다양한 도구들을 정확한 목적과 기능을 알고 적절한 판단(최적화)을 가지고 사용해야한다. 그래야 전문가가 될 수 있음.



### React의 state는 "변경"을 다루기 위한 요소.

"Re-rendering"이라는 주제에서 다뤄진다.



우리는 이 state를 일관성과 효율을 위해 DRY 원칙을 따르는 SSOT를 만든다.



### state는 비즈니스 로직과 유기적으로 연결된다.

쉽게 생각해서 state가 데이터랑 이꼴\*3(js이니까)  이라고 생각하면 그냥 막 만들면 됨.

그냥 변수 선언해서 가져다가 쓰면 됨.



그런데 state 포인트는 <mark style="background-color:red;">비즈니스 로직(핵심 데이터)가 변경되면 다같이 유기적으로 변경되는 아름다운 구조</mark>를 만드는게 목표.&#x20;

\=> 이 역시 state는 '변경'을 다루는 요소라는 것에 저절함.

\=> 아 ... 그래서 setState를 하면 전체  렌더링을 하네(React 개발한 사람이 이 부분을 고려했다는것)

\=> 왜? state는 '변경'을 다루는 요소니까

\=> 또한 우리의 비즈니스 로직에 관여된 데이터들은 빈번하게 변경이 됨.

\=> 댓글이 달린다거나, 게시물이 삭제된다거나 등등

