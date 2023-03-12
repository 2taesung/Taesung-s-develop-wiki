# 관심사의 분리(SoC)

하나의 시스템은 작은 부품이 모여서 만들어진다. 우리는 이미 작은 컴포넌트를 합쳐서 더 큰 컴포넌트를 만드는 방식으로 개발하고 있다.



어떤 기준을 사용할 수 있을까? 흔히 사용되는 Layered Architecture에선 사용자에게 가까운 것과 사용자에게서 먼 것으로 구분한다. 가장 가까운 건 UI를 다루는 부분, 그 다음엔 Business Logic을 다루는 부분, 그 너머에는 데이터에 접근하고 저장하는 부분으로 나눌 수 있게 된다. 각 부분은 하나의 역할, 하나의 관심사로 격리됨으로써 복잡도를 낮추게 된다.



사람 - 스위치 - 모터 -> 바퀴

&#x20;            (UI)     (로직)   (data)



널리 알려진 MVC로 거칠게 매핑하면 다음과 같다.

1. Input: 프로그램 시작
2. Process: 프로그램 초기화
3. Output: 사용자에게 초기 UI 보여주기
4. Input: 사용자의 입력
5. Process: 사용자의 입력에 따라 처리
6. Output: 처리 결과 보여주기
7. Input: 사용자의 또 다른 입력
8. …반복…

거대한 프로그램이 아니라고 해도 흔히 Input → Process → Output이란 3단계로 코드를 적절히 구분만 해도 코드를 이해하고 유지보수하는데 크게 도움이 된다. 하나의 Output은 다시 사용자에게 Input을 요청하게 되고, 일반적인 프로그램은 다음과 같이 계속 순환하는 구조가 된다.



널리 알려진 MVC로 거칠게 매핑하면 다음과 같다.

* Controller → Input
* View → Output
* Model → Process

\
\
보면 위의 Input, Process, Output 설계, MVC 패턴,  Layered Architecture, 함수형 프로그래밍 등등

이 모든게 말하는게 결국&#x20;

액션(외부로부터 영향, 인자, UI 인터랙션) -> 계산(로직) -> 데이터(output, 결과, view)

말장난인가 싶을 정도.



이 셋으로 관심사의 분리를 할 수 있음.



물론 위의 말대로 단순하게 카테고리로 묶이는건 내 지식이 짧다라는 반증이기도 하다.

왜냐하면 하나하나마다 세부적으로 다른 의미들이 있긴 할테니까&#x20;



그러나 결국 우리가 이런걸 배우고 연구하고 하는 이유는&#x20;

사람을 만들기위해 사람을 구성하고 있는 세포들을 어떻게 잘 만드는가.



라고 생각하고 있던 와중에

아래의 멋진 글을 읽었는데 글을 정말 깔끔하게 잘쓴다고 생각이 들었다.



이 분 같은 경우 관심사의 분리, 객체지향 이 두가지를 가지고 글을 쓰셨는데

관심사의분리와 단일책임원칙 간의 뭔가 정리가 따로 없었다.

이 두가지를 가지고 혼란스러워하는 내가 잘못된거 같기도 하고 ....

아무튼 더 정확하게는 강의 다 듣고 질문 하는걸로.



[https://velog.io/@eddy\_song/separation-of-concerns](https://velog.io/@eddy\_song/separation-of-concerns)

[https://velog.io/@eddy\_song/alan-kay-OOP](https://velog.io/@eddy\_song/alan-kay-OOP)






