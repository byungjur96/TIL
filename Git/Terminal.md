# Terminal을 이용하여 github 사용하기

### 1. Personal Access Token 발급받기

최근 Github에서는 터미널에서 password를 통해 권한을 얻는 방법을 제한하였다. 따라서 Github 내에서 토큰을 발급받아야 한다.

참고자료: [깃허브 토큰(Token) 생성하는 법]("https://hoohaha.tistory.com/37)

### 2. Github Configuration 설정하기

모든 설정을 진행하여 push를 해주어도 내 Github 페이지 내에서 configuration이 표시되지 않는 경우가 있다. 이것은 내가 commit하지 않은 것으로 인식되는 것인데, 이걸 수정하기 위해서는 터미널 내에서 git 정보의 이메일 주소와 내 github 이메일 주소가 동일해야 한다.

1. 아래 명령어를 통해 터미널 내의 이메일 주소를 확인할 수 있다.
    ```bash
    git config user.email
    ```
2. 이메일 주소가 동일하지 않다면 아래 명령을 통해서 이메일 주소를 설정해줄 수 있다.
    ```bash
    git config --global user.email 이메일주소
    ```

참고자료: [분명 commit을 했는데 왜 contribution 그래프는 안채워지지..?]("https://velog.io/@think2wice/Github-분명-commit을-했는데-왜-contribution-그래프는-안채워지지")

