## Node.js

#### Node.js 버전 문제

---

![](https://github.com/byungjur96/TIL/blob/master/AWS%20Lambda/img/node%20update.png)

처음 `create`  함수를 만들었을 때 `invoke` 가 되지 않는 문제가 있었습니다.

Node.js 버전이 8.10 이하인 경우 발생하는 오류입니다.

Node.js 버전을 터미널을 통해 업데이트하는 방법은 다음과 같습니다. 



**1. Node.js 버전 확인하기**

```bash
node -v
```

컴퓨터에 설치되어 있는 Node.js의 버전을 확인합니다.

**2. n 모듈 설치하기**

```bash
sudo npm install -g n
```

n은 Node.js의 버전을 관리해주는 플러그인입니다. `npm` 을 이용하여 설치해줍니다.

**3. Node.js 설치하기**

```bash
n stable
```

Node.js table 을 설치하기 위해서 위와 같은 명령어를 입력해줍니다.

latest나 lts, 또는 특정 버전의 Node.js를 설치하고자 할 때에는 위의 `stable` 명령어 대신에 해당하는 버전을 입력합니다.



참고자료: [Node.js 버전 관리하기 (설치 & 업데이트)](https://futurecreator.github.io/2018/05/28/nodejs-npm-update-latest-or-stable-version/)

