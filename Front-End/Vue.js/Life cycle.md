## Life cycle

Vue.js 2.0에서부터는 Life Cycle이 존재한다.

Vue.js의 라이프 사이클은 크게 Creation, Mounting, Updating, Destruction 4개로 나눌 수 있다.

아래의 이미지는 Vue.js의 라이프 사이클을 나타낸 것이다.

![](https://github.com/byungjur96/TIL/blob/master/Front-End/Vue.js/vue_LifeCycle.png)



#### Creation

---

컴포넌트가 DOM에 추가되기 전의 상황이다. 따라서 DOM에 접근하거나 `this.$el` 을 사용할 수 없다.

해당 훅: `beforeCreate`, `created` 



#### Mounting

---

초기 렌더링 직전 상황이다. 컴포넌트에 직접 접근할 수 있다. 초기 렌더링 직전에 돔을 변경하고자 하면 이 단계를 활용할 수 있다. 그러나 컴포넌트 초기에 세팅되어야 할 데이터 패치는 `created` 단계를 사용하는 것이 권장된다고 한다.

해당 훅: `beforeMount`, `mounted` 

#### Updating

---

컴포넌트에서 사용되는 반응형 속성들이 변경되거나 다시 렌더링되는 경우 발생된다.

해당 훅: `beforeUpdate`, `updated` 

#### Destruction

---

`instance` 가 제거되는 상황이다. `Event Listener` 를 제거하거나 `reactive subscription` 을 제거하고자 할 때에는 `beforeDestroy` 를, `instance` 가 제거된 후에는 `destroyed` 를 사용하면 된다.

해당 훅: `beforeDestroy`, `destroyed` 



참고자료: [Vue.js 2.0 라이프사이클 이해하기](https://medium.com/witinweb/vue-js-라이프사이클-이해하기-7780cdd97dd4), [라이프 사이클](https://beomy.tistory.com/47) 