## Intro

#### Vue.js란

------

- Google Creative Lab에서 일하던 *Evan You*에 의해 2013년 12월 개발.
- UI를 빠르게 개발하기 위해서!



#### MVVM 패턴

------

- Model-View-ViewModel의 줄임말
- 애플리케이션 로직과 UI의 분리
- View: HTML과 CSS
- ViewModel: View의 실제 논리 및 데이터 흐름 (상태와 연산)
- Model: 도메인 특화 데이터



#### Vue 프로젝트 탬플릿

- `Simple` : 단일 HTML 파일 (CDN 방식)
- `Browserify` : Browserify + Vueify 조합. 대규모 애플리케이션 개발용.
- `Browserify-simple` : 빠른 프로토타이핑용.
- `Webpack` : Webpack + Vue-Loader 조합. hot-reload, linting, 단위 테스트 기능을 제공.
- `Webpack-Simple` : 빠른 프로토타이핑용.
- `PWA` :  PWA를 위한 라이브러리가 추가되어 있음.



#### 주의할 점

------

- `<head>` 태그 맨 처음에 `<meta charset="utf-8">` 을 넣어서 한글이 깨지지 않도록 합니다. 