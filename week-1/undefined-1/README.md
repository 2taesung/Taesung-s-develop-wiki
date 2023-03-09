# 번들러(빌드)

번들러의 핵심 목적은&#x20;

* ts, jsx, tsx 등 -> JS로 트랜스파일링
* 플러그인 추가
* 폴리필(Polyfill) 적용

[Parcel vs Rollup vs Webpack 비교](https://velog.io/@subin1224/Parcel-vs-Rollup-vs-Webpack-%EB%B9%84%EA%B5%90)

\=> Webpack의 문제점을 인식해 다른 애들이 나옴

\=> 그러나 장단점들이 있어 적절한 상황에 적용이 결론.



최신 트렌드는 번들링(빌드) 속도가 왜이렇게 오래걸리냐&#x20;

속도를 빠르게 개선해서 개발 경험을 향상시키자

그런데 기본적으로 번들링의 작업들이 NodeJS 싱글 스레드 구조다 보니 한계 존재.



그래서 Native 영역에서 성능을 높임

* Golang -> [esbuild](https://esbuild.github.io/) (안정성 높음)
* Rust -> [SWC](https://github.com/swc-project/swc)

여기에이들을 이용해 Node.js로 한단계 래핑하여 속도를 개선

* esbuild -> Vite, Snowpack

## [Webpack → Vite: 번들러 마이그레이션 이야기](https://engineering.ab180.co/stories/webpack-to-vite)





