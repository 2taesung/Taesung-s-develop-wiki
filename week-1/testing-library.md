# Testing Library

Jest에는 RSpec의 let 지원 x

### 기본적인 테스트 코드

```javascript
test('add', () => {
  expect(1+2).toBe(3);
});s
```

> npm test

package.json

```json
  "scripts": {
    "start": "parcel --port 8080",
    "build": "parcel build",
    "check": "tsc --noEmit",
    "lint": "eslint --fix --ext .js,.jsx,.ts,.tsx .",
    "test": "jest",
    "coverage": "jest --coverage --coverage-reporters html",
    "watch:test": "jest --watchAll"
  },
```

> npm run watch:test

\=> 수정시 계속 체크해준다.

### 자연스러운 TDD 순서

테스트 코드 먼저 => 구현부&#x20;

테스트를 믿고 진행

### BDD 스타일의 테스트 코드

BDD??

```javascript
describe('add', () => {
  it('returns sum of two numbers', () => {
    expect(add(1, 2)).toBe(3);
  });
```

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

\=> 설명이 표시되는걸 볼 수 있음

\=> 이렇게 간단하게 쓰면 재미없고 context를 활용해 다양하게 사용할 수 있음

\=> 아무쪼록 더 표현력이 좋아지고, 좀 더 고민할 기회를 제공함.&#x20;

\=> 단순히 막무가내로 코딩하는게 아니라 엣지 케이스들을 고려하게 되는 것 같음

\=> 여러가지 생각을 할수록 버그 없고 멋진 코드가 될 가능성이 높아질듯.



context 활용

```typescript
function add(x: number, y: number): number {
  return x+y;
}

const context = describe;

describe('add 함수', () => {
  
  context('하나의 양수와 음수가 주어지면', () => {
    it('항상 하나의 양수보다 작은 값을 돌려준다', () => {
      expect(add(1, -2)).toBeLessThan(1);
    })
  })
});
```

{% hint style="info" %}
처음 테스트를  실행했을때 해당 에러가 발생했는데 이는 test.config 파일에서 중첩으로 (지우라는거 안지우고 ;;) './jest.setup' 을 했기 때문에 이걸 다시 덮으면 필수적으로 추가해야하는 option을 설정 안해서 생기는 에러였음

```javascript
setupFilesAfterEnv: [
  '@testing-library/jest-dom/extend-expect', //는 사실 설치를 위에서 하긴 함
  // './jest.setup', //이건 안쓴다 지워
],
```



tsl@pc:\~/mt/my-app$ npm test

> my-app@1.0.0 test jest

● Validation Error:

Module ./jest.setup in the setupFilesAfterEnv option was not found. is: /home/tsl/mt/my-app

Configuration Documentation: https://jestjs.io/docs/configuration
{% endhint %}

```
tsl@pc:~/mt/my-app$ npm test

> my-app@1.0.0 test
> jest

● Validation Error:

  Module ./jest.setup in the setupFilesAfterEnv option was not found.
         <rootDir> is: /home/tsl/mt/my-app

  Configuration Documentation:
  https://jestjs.io/docs/configuration
```
