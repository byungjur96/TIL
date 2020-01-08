## Component 간 통신

기본적으로 Vue.js는 부모에서 자식으로만 데이터를 전달해야 하는 단방향 데이터 흐름의 통신 규칙을 따른다.

하지만 자식 컴포넌트에서 부모 컴포넌트로 정보를 전달할 수 있는 방법이 아예 없는 것은 아니다.

Vue.js에서 Component 간의 통신은 props, event 두 개로 구분할 수 있다.

props란 부모 컴포넌트에서 자식 컴포넌트로 데이터를 전달하는 것을 의미힌다.

event는 자식 컴포넌트가 event를 발생시켜서 부모 컴포넌트로 메세지를 보내는 것을 의미한다.



#### 이벤트 발생

---

이벤트를 발생시키기 위해서는 자식 컴포넌트 안에 아래와 같은 코드를 추가한다.

```javascript
// 하위 컴포넌트의 내용
this.$emit('이벤트 명');
```

이후 해당 이벤트를 수신하기 위해서는 부모 컴포넌트에 아래와 같은 코드를 작성한다.

```html
<!-- 상위 컴포넌트의 템플릿 -->
<div id="app">
  <child-component v-on:이벤트 명="상위 컴포넌트의 실행할 메서드 명 또는 연산"></child-component>
</div>
```

전체 예시 코드는 아래와 같다.

```javascript
// 자식 컴포넌트 : childComponent
var childComponent = {
  methods: {
    sendEvent: function() {
      this.$emit('update');
    }
  }
}

// 상위 컴포넌트 : root 컴포넌트
new Vue({
  el: '#app',
  components: {
    'child-component': childComponent
  },
  methods: {
    showAlert: function() {
      alert('event received');
    }
  }
})
```

```html
<!-- 부모 컴포넌트 -->
<div id="app">
  <child-component v-on:update="showAlert"></child-component>
</div>
```



#### props 속성

---

props 속성을 사용하기 위해서는 부모/자식 컴포넌트에 다음과 같은 코드를 추가해줘야 한다.

```javascript
// 자식 컴포넌트의 내용
var childComponent = {
  props: ['프롭스 속성 명']
}
```

```html
<!-- 부모 컴포넌트의 템플릿 -->
<div id="app">
  <child-component v-bind:프롭스 속성 명="상위 컴포넌트의 data 속성"></child-component>
</div>
```

아래는 props 속성을 사용한 실제 예시다.

```javascript
// 자식 컴포넌트 : childComponent
var childComponent = {
  props: ['propsdata'],
  template: '<p>{{ propsdata }}</p>'
}

// 부모 컴포넌트 : root 컴포넌트
new Vue({
  el: '#app',
  components: {
    'child-component': childComponent
  },
  data: {
    message: 'hello vue.js'
  }
})
```

```html
<div id="app">
  <child-component v-bind:propsdata="message"></child-component>
  <!-- 위의 출력 결과는 hello vue.js -->
</div>
```



⚠️ 모든 코드는 아래 참고 자료에 나온 코드입니다.



참고 자료: [이벤트 발생]("https://joshua1988.github.io/vue-camp/vue/event-emit.html#이벤트-발생-코드-형식"), [props 속성](https://joshua1988.github.io/vue-camp/vue/props.html#props-속성-코드-형식), [[Vue.js]컴포넌트(고급: Custom Events)]("https://beomy.tistory.com/57") 