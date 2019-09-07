## Media Query

#### Media Query가 적용되지 않는 문제

---

얼마 전에 새로 vue 프로젝트를 시작해서 media query를 CSS에 계속 적용했는데 적용이 되지 않았다.

생활코딩에 질문을 한 결과 해결책을 찾았는데 생각보다 굉장히 기본적인 부분을 내가 놓치고 있었다.

바로 `<head>` 태그 안에 `<meta>` 태그를 빼먹은 것이다.

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

위의 코드를 `<head>` 태그 안에 넣어주어야 media query가 적용된다.

보통 VSCode나 Sublime Text에서 사용할 때에는 Emmet을 이용해서 이 코드의 중요성을 간파하고 있었다.

위의 `<meta>` 태그의 attribute 들은 아래 첫번째 참고자료에 자세히 언급되어 있다.



참고로 vue.js 어플리케이션 내에서 viewport를 지정하기 위해서는 전체 프로젝트 내의`'index.html` 내에 선언해주면 된다.



참고자료: [viewport 사용법]("https://offbyone.tistory.com/110?fbclid=IwAR0eCYZd0rJ8cxj5nqOrDlop-Q6cAcFCgwMjNI_xk4BwLIJruW46RNXpXTc"), [Set viewport meta-tag in vue.js application](https://stackoverflow.com/questions/53285704/set-viewport-meta-tag-in-vue-js-application)

