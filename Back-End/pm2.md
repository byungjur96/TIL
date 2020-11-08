## pm2

#### pm2란?

---

- pm2는 프로세스 관리툴이다.
- 접속이 끊어져도 해당 파일이 계속 실행됨.



### 기본 커멘드

---

- `pm2 start <file>` : `<file>` 을 실행한다. 
  - `--name` :이름을 정해줄 수 있음. (나중에 해당 이름으로 커멘드 가능)
  - `--watch` : 파일이 수정된 경우 자동 재시작
  - `--no-autorestart` : 프로세스 다운 시 자동 재시작 미설정
- `pm2 list` : 전체 프로세스 서버/상태를 확인.

- `pm2 stop <proc>` : 해당 프로세스 정지.
- `pm2 delete <proc>` : 해당 프로세스 삭제.
- `pm2 show <proc>` : 해당 프로세스 정보 확인.
- `pm2 monit` : 모니터링 대시보드.



#### 참고자료

- [(가비아) 프로세스 관리 도구 사용하기]("https://wiki.gabia.io/nodejs/pm")
- [(node.js) 프로세스 관리도구 pm2]("https://m.blog.naver.com/PostView.nhn?blogId=pjt3591oo&logNo=221034901679&proxyReferer=https:%2F%2Fwww.google.com%2F")