# SRP 수단

### Extract Function

[Extract Function](https://refactoring.com/catalog/extractFunction.html)

```javascript
function printOwing(invoice) {
  printBanner();
  let outstanding  = calculateOutstanding();

  //print details
  console.log(`name: ${invoice.customer}`);
  console.log(`amount: ${outstanding}`);  
}
```

\=> 다음 코드를 보면 주석이 있음

\=> 주석이 있는 이유는 아래의 코드가 <mark style="background-color:red;">'작성된 코드만으로 불충분하다는 단서'</mark>

\=> 나는 지금까지 주석은 최대한 달면 좋은것이라고만 배워왔다.

\=> 하지만 해당 예시처럼 함수의 변수명으로 주석의 역할을 해줄 수 있음.

\=> 무조건은 아니겠지만 부연설명이 필요한 코드다? 하면 무언가 더 필요한 코드라는 단서가 되고 그 수단 중 하나가 함수로 만드는게 가능

```javascript
function printOwing(invoice) {
  printBanner();
  let outstanding  = calculateOutstanding();
  printDetails(outstanding);

  function printDetails(outstanding) {
    console.log(`name: ${invoice.customer}`);
    console.log(`amount: ${outstanding}`);
  }
}
```

\=> 함수를 만들면서 함수명이 주석의 역할을 맡게 되고 주석은 빠지게 되었다.

\=> 주석은 쓰고 끝이지만 함수는 다양한 활용과 재활용성,  확장성을 고려해볼 수 있게 된다.

\=> 특히, 일급 객체인 js 에서는 함수 활용을 더 적극적으로 해야할 필요성이 있다.



