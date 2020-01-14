## Install (Docker)

#### Docker에 Kaldi 설치하기

---

Docker 커멘트 창에 아래 명령어를 입력하면 됩니다.

 ```sh
docker run -v ~/Desktop/share_kaldi:/opt/kaldi/share \
-e USER=exp_user \
--name kaldi \
-it kaldiasr/karldi:latest bash # GPU 환경에서는 -it --runtime=nvidia kaldiasr/kaldi:gpu-latest bash
 ```



##### `docker run` 명령어

- Container를 생성하고 시작하는 명령어

- Options
  - `docker run --name <name>` : Container 이름 설정
  - `docker run -v <host_dir>:<container_dir>` :데이터 볼륨을 설정 (호스트와 공유할 디렉토리/파일 설정)
  - `docker run -e` : Container의 환경 변수를 설정
  - `docker run -it` : `-i` 옵션과 `-t` 옵션을 합친 것. 뒤에 `bash` 를 적어야 `bash` 명령어를 인식함.
    - `-i` (interactive): 표준 입력(STDIN)을 활성화. 입력에 대한 출력을 보여줌.
    - `-t` : Shell을 표시해주는 옵션. `bash` 사용을 위해서는 꼭 필요함.



#### 설치된 Kaldi Container 실행하기

---

```sh
docker start kaldi && docker attach kaldi
```



참고자료: [가장 빨리 만나는 Docker 20장 - 28. run]("http://pyrasis.com/book/DockerForTheReallyImpatient/Chapter20/28"),  [3. 도커의 몇 몇 run 옵션들]("http://blog.naver.com/PostView.nhn?blogId=alice_k106&logNo=220340499760&parentCategoryNo=7&categoryNo=&viewDate=&isShowPopularPosts=true&from=search"), [Docker Run Reference]("https://docs.docker.com/engine/reference/run/")  