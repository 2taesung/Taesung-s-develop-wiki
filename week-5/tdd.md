# TDD

### **TDD란?**

**테스트 코드를 먼저 작성하는,**&#x20;

막연하게 접근하는게 아니라.&#x20;

이런게 있고 이런걸 넣으면 이렇게 돼!&#x20;

라는 구체적인 설계(인터페이스, 스펙)를 하고&#x20;

**구현에 들어가는 것을 말한다.**



### TDD Cycle

1. Red -> 실패하는 테스트 코드를 작성. 인터페이스와 스펙에 집중한다.
2. Green -> 재빨리 테스트를 통과시킨다. 올바른 방법이 아니어도 괜찮다
3. Refactor -> 리팩터링을 통해 코드를 올바르게 만든다. TDD에서 가장 중요한 부분이지만, 관과될 때가 많다.

\=> 캔트백(TDD창시자) 왈 2번을 빨리하기 위해서 죄악을 저질러도 괜찮다라고....

\=> 우리가 이걸 처음부터 완벽하게 하려고 하면 너무 힘들다.

\=> 그러나! 2번을 최대한 빠르게 해결한 후에 이것저것 바꿔보면서 해보는거야

\=> 그러다가 테스트가 깨진다? 그러면 다시 돌아가서 테스트에 맞추고..



\=> 프로그래밍, 소프트웨어는눈에 보이지 않는것.

\=> 이것을 우리는 눈에보이는 것으로 바꾸는 것이다.