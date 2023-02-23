# useCustom

> [Reusing Logic with Custom Hooks](https://beta.reactjs.org/learn/reusing-logic-with-custom-hooks)

> [자신만의 Hook 만들기](https://ko.reactjs.org/docs/hooks-custom.html)

로직을 재사용하기 위한 제일 쉬운 방법.

평범하게 Extract Function을 수행하면 된다.&#x20;

```jsx
function useFetchProducts() {
	const [products, setProducts] = useState<Product[]>([]);
	
	useEffect(() => {
		const fetchProducts = async () => {
			const url = '<http://localhost:3000/products>';
			const response = await fetch(url);
			const data = await response.json();
			setProducts(data.products);
		};

		fetchProducts();
	}, []);

	return products;
}
```

컴포넌트 코드도 명확해지고, setProducts가 실수로 잘못 쓰일 문제까지 해소됨.



\=> 일급객체이기 때문에 return으로 setProducts를 또 해줄수도 있음 참고.
