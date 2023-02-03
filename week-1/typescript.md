# TypeScript

### interface vs type

interface만 알고 있었는데 기능이 거의 비슷한 type이라는게 있다.

[interface vs type docs](https://www.typescriptlang.org/ko/docs/handbook/2/everyday-types.html#%ED%83%80%EC%9E%85-%EB%B3%84%EC%B9%AD%EA%B3%BC-%EC%9D%B8%ED%84%B0%ED%8E%98%EC%9D%B4%EC%8A%A4%EC%9D%98-%EC%B0%A8%EC%9D%B4%EC%A0%90)

일반적인 개발자는 interface를 많이 사용 아샬님은 type을

이 둘의 핵심적인 차이는 타입은 새 프로퍼티를 추가하도록 개방될 수 없는 반면, 인터페이스의 경우는 항상 확장될 수 있다는 점.



### 배열을 Tuple로 더 깐깐하게 할수도 있음

```
let anythings: any[];

anythings = ['hp', 256];

let pair: [string, number];

pair = ['hp', 256];
```



### 매개변수를 제한하거나 할 때, 매우 유용하게 쓸 수 있

예를들어, 'food', 'toy', 'bag' 으로 매개변수를 특정해 제한하고 추론을 유도할 수 있

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

이걸 제한하는 기능만 생각할수도 있는데

function 같은데서 특히 '추론'을 많이 사용하고 효과적이다.

```
type Category = 'food' | 'toy' | 'bag';
function fetchProducts({ category }: { category: Category }) {
  console.log(`Fetch ${category}`);
}
```

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

\=> 함수를 사용할 때, 굉장히 직관적으로 변하고 효율적으로 되고 먼 훗날에 함수를 보더라도 더 이해하기 쉬워질듯 함.(이건 아직 내 추측)
