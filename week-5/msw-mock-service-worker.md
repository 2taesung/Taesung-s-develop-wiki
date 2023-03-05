# MSW (Mock Service Worker)

> [MSW](https://mswjs.io/)

> [Service Worker API](https://developer.mozilla.org/ko/docs/Web/API/Service\_Worker\_API)

> [아샬의 Mock Service Worker (MSW)](https://github.com/ahastudio/til/blob/main/mock-api/msw.md)

> [Mocking REST API](https://mswjs.io/docs/getting-started/mocks/rest-api)

> [Integrate mocking into Node](https://mswjs.io/docs/getting-started/integrate/node)



코드 레벨이 아니라 네트워크 레벨에서 가짜 구현.&#x20;

MSW의 SW가 서비스 워커다.

'서비스워커' 알지.

\=> pwa를 만들때 꼭 필요한 요소.

* <mark style="background-color:orange;">mocking 하면 내 맘대로 컨텐츠를 만들 수 있다는 셈인데 의존적인 것들 역시 테스트를 할 수 있어야하는거 아닐까?</mark>

<figure><img src="../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

\=> '설계적 요류' 가 있는 신호라는게 아직 이해가 되지는 않음.

\=> 더 공부를 해보면서 해결해나가자



MSW 패키지 설치

```bash
npm i -D msw
```

`jest.config.js` 파일의 “setupFilesAfterEnv” 속성에 `setupTests.ts` 파일 추가.

```jsx
module.exports = {
	testEnvironment: 'jsdom',
	**setupFilesAfterEnv**: [
		'@testing-library/jest-dom/extend-expect',
		'**<rootDir>/src/setupTests.ts**',
	],
	transform: {
		'^.+\\\\.(t|j)sx?$': ['@swc/jest', {
			jsc: {
				parser: {
					syntax: 'typescript',
					jsx: true,
					decorators: true,
				},
				transform: {
					react: {
						runtime: 'automatic',
					},
				},
			},
		}],
	},
};
```

`src/setupTests.ts` 파일

```jsx
import server from './mocks/server';

beforeAll(() => server.listen({ onUnhandledRequest: 'error' }));

afterAll(() => server.close());

afterEach(() => server.resetHandlers());
```

`src/mocks/server.ts` 파일

```jsx
// msw 가 -D 로 dev 상태일 때만 존재하게 만들어놔서 떡 하니 있으면 lint를 뿜기도 함(난 안뿜기는함)
// eslint-disable-next-line import/no-extraneous-dependencies
import { setupServer } from 'msw/node';

import handlers from './handlers';

const server = setupServer(...handlers);

export default server;
```

`src/mocks/handlers.ts` 파일

→ Express의 경험을 살려보자!

```jsx
import { rest } from 'msw';

const BASE_URL = '<http://localhost:3000>';

const handlers = [
	rest.get(`${BASE_URL}/products`, (req, res, ctx) => {
		const { products } = fixtures;

		return res(
			ctx.status(200),
			ctx.json({ products }),
			);
		}),
	];

export default handlers;
```



\`App.text.tsx\`

````typescript
import { render, screen, waitFor } from '@testing-library/react';

import App from './App';

test('App', async () => {
	render(<App />);
	
	await waitFor(() => {
		screen.getByText('메가반점');
	});
});
```
````



<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

\=> node 에는 fetch가 없다.

\=> msw 로 fetch 까지 구현을 해버리니 이제는 문제가 생기는것.



setupTests.ts

```typescript
import 'whatwg-fetch';

import server from './mocks/server';

beforeAll(() => server.listen({ onUnhandledRequest: 'error' }));

afterAll(() => server.close());

afterEach(() => server.resetHandlers());
```

```
import 'whatwg-fetch';  추가
```

<mark style="background-color:orange;"></mark>

<mark style="background-color:orange;">=> 근데 솔직히 내용을 보면 거의 express 수준의 코드 작업이 필요..</mark>

<mark style="background-color:orange;">=> 그냥 express로 BFF(Backend For Frontend)를 만드는건...?</mark>

<mark style="background-color:orange;">=> 왜냐하면 어차피 FE도 Backend를 하는 트렌드인듯?</mark>

<figure><img src="../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

\=> MSW가 처음 해보니까 어렵게 느껴지는 것일 수 있음.

\=> 직접 실습 해보며 더 판단해보자

\=> 근데 백엔드 만들줄 아는 내 입장에서 도구를 하나 더 가지고 있는것도 뭐 문제될건 없음.



