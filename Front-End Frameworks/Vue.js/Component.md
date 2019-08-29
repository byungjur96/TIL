## Component

###Component 등록하기

---

#### 1) 전역 등록

Vue.js에서 Component를 전역 등록하려면 아래와 같이 선언하면 됩니다.

```javascript
Vue.component('my-component', {
  // 옵션
})
```

`webpack` 기준으로, `main.js` 에 위와 같이 선언해주면 Component가 전역 등록됩니다.



**:warning: Component를 등록하는 것과 Vue 인스턴스를 만드는 것은 다릅니다!**

Vue의 인스턴스를 만드는 것은 아래와 같습니다.

```javascript
new Vue({
  el: '#some-element',
  // 옵션
})
```



#### 2) 로컬 등록

Vue.js에서 Component를 특정 인스턴스/Component 안에서만 사용할 수 있도록 등록할 수도 있습니다.

이때에는 인스턴스의 옵션으로 선언하면 됩니다.

```javascript
new Vue({
  // ...
  components: {
    // <my-component> 는 상위 템플릿에서만 사용할 수 있습니다.
    'my-component': Child
  }
})
```



`Single File Component` 로 선언되어 있는 경우 아래와 같이 선언할 수 있습니다. (:warning: **확인 필요!**)

```javascript
import MyComponent from './my-component.vue';

export default {
	// ...
  components: {
		MyComponent
  },
  // ...
}
```

:exclamation: Component를 선언해주어야 부모-자식 Component 관계가 성립합니다.​

:exclamation: 지역 선언을 해주면 컴포넌트 이름을 태그명처럼 사용할 수 있습니다.



참고자료: [How to Solve "Unknown Custom Element" in Vue]("https://michaelnthiessen.com/solve-unknown-custom-element-vue"), [공식 document]("https://kr.vuejs.org/v2/guide/components.html#%EC%BB%B4%ED%8F%AC%EB%84%8C%ED%8A%B8-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0") 



### Single File Component

---

`Single File Component` 는 전역 수준 컴포넌트의 몇 가지 문제점을 해결하기 위해 나온 개념입니다.

전역 수준 컴포넌트의 단점은 다음과 같습니다.

* 빌드 단계가 없으므로 ES6, TS와 같은 최신 JS 문법을 사용할 수 없습니다. 따라서 HTML 내부에 직접 ES6 버전의 코드를 작성해야 합니다.
* 컴포넌트들은 고유한 스타일 정보를 포함하는 경우가 많은데, 전역 컴포넌트에서는 CSS 스타일을 빌드하고 모듈화할 수 있는 기능을 제공하지 않습니다.
* HTML 파일 안에 여러 개의`<template>` 태그가 작성되어 각각을 구분하기 어렵습니다. 또한 각 `<template>` 마다 고유한 id를 부여하고 고유한 이름 역시 정해야 합니다.



`Single File Component` 는 위와 같은 문제를 해결하기 위해 나왔습니다. 

`Single File Component` 는 `<template>`, `<script>`, `<style>` 세 부분으로 구성되어 있는 `.vue` 라는 확장자 파일입니다.

`vue-loader` 는 이 파일을 파싱하고 하나의 모듈로 조합합니다.



참고자료: Quick Start Vue.js, [공식 document]("https://kr.vuejs.org/v2/guide/single-file-components.html")

