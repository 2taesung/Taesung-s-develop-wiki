# 개발 환경 세팅

{% hint style="warning" %}
우리는 Node.js 를 기반으로 개발을 하는데 왜 이게 어렵냐면 계속 바뀌기 때문.&#x20;

정리하고 있는 지금도 버전이 달라지고 있음.

그러므로 앞으로 전체적인변흐름을경파악하고 변경 대응할 수 있는 능력을 키우는게 중요
{% endhint %}

\=> 이 능력은 어떻게 키우는가?&#x20;

<mark style="background-color:orange;">=> 강의를 들으며 찾아보고 못찾으면 구체적으로 질문.</mark>

\=> 내 생각으로개발할때 개발환경을 항상 생각하면서 개발하는 습관을 갖는것?



### JavaScript(Node.js) 개발 환경 세팅(global)

1.  Node.js

    [https://nodejs.org/](https://nodejs.org/)
2. Node.js Version manager

&#x20;    우리가 NVM으로 익숙한 것.

&#x20;    속도가 빠른 fnm을 사용.

&#x20;    \- fnm (Fast Node Manager)

&#x20;      [https://github.com/Schniz/fnm](https://github.com/Schniz/fnm)

{% hint style="info" %}
내 환경은 wsl이

.fnm, .node 등의 글로벌 파일들은 시스템 자체인 /home 에 존재

더불어 React는hot reloader 가 mnt/\~ 에서는 작동이 안되기 때문에 /home 이후인 곳에 폴더를 위치시킨다.
{% endhint %}

### TypeScript + React + Jest + Parcel

> mkdir \<my-app>
>
> cd \<my-app>

1. npm

> npm init

옵션들이 많이 나오는데 한번 쭉 읽어보아라.

> npm i -y //추가적인 옵션 질문들에 걍 다 yes 하겠다.

package.json

```
{
  "name": "my-app",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC"
}
```

<mark style="background-color:orange;">npm 버전에대한 이야기는 없네 => 강의 듣고 내용 없으면 질문</mark>

![](../.gitbook/assets/image.png)

2. .gitignore

```
/node_modules/ //폴더라는 의미가 담김
or
node_modules/ //현재 위치
or
node_modules //아몰랑 이 이름 다.
```

[https://www.toptal.com/developers/gitignore/](https://www.toptal.com/developers/gitignore/)



3. typescript

> npm i -D typescript









