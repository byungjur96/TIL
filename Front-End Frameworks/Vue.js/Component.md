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

:exclamation: Component를 선언해주어야 부모-자식 Component 관계가 성립한다.​

