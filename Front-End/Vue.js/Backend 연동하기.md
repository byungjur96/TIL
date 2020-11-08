## Backend 연동하기 (배포)

`root` 폴더 안에  `vue.config.js` 파일을 생성한 뒤 아래와 같이 입력한다.

```JavaScript
module.exports = { 
  // api 요청이 있을때 어디에서 처리할지를 설정
  devServer: { 
    proxy: { 
      '/api': { 
        target: 'http://localhost:3000/api',
        changeOrigin: true, 
        pathRewrite: { 
          '^/api': ''
        } 
      } 
    } 
  },
  //  배포 파일의 위치를 지정
  outputDir: '../backend/public',
  // 외부 파일 참조 경로를 지정 (default: '/')
  publicPath : '',
}
```



#### 참고자료 

- [`vue.config.js` 에서 build 시에만 publicPath 변경 방법]("https://kabkee.github.io/vue-cli/vue-cli-publicPath/#publicpath-%EA%B0%80-%EB%AC%B4%EC%97%87%EC%9D%B8%EA%B0%80")

- [Vue.js + Express + MySQL로 Node API 서버 구성하기 Quick Start — Part 1]("https://medium.com/hivelab-dev/vue-express-mysql-part1-98f68408d444")

  

