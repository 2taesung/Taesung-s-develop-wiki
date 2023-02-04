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

### BDD 스타일의 테스트 코드

BDD??





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
