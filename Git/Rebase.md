# Rebase

### 1.  rebase의 위험성

> 이미 공개 저장소에 push한 commit을 rebase 하지 마라!

rebase는 기존의 commit을 단순히 수정하는 것이 아니라 내용은 같지만 다른 commit을 새로 만들기 때문!

다른 사람과 함께 일하는 경우 코드가 엉망이 될 수 있다.



참고자료: [Git 브랜치 - Rebase 하기](https://git-scm.com/book/ko/v2/Git-브랜치-Rebase-하기) 



### 2. commit 작성자 이름 변경하기

1. **`commit hash` 값 찾기**

   `git log` 명령어를 통해서 변경할 대상 바로 직전 커밋의 hash 값을 확인한다.

2. **`rebase` 명령어 입력**

   ```shell
   git rebase -i -p `<commit hash>`
   ```

   `<commit hash>` 위치에 변경할 commit 바로 이전 commit의 hash 값을 적는다.

3. **commit 설정 변경**

   위의 명령어를 입력하면 자동으로 vi 에디터가 열린다.

   파일의 내용은 아래와 같다.

   ```bash
   # 출처: MadPlay's MadLife
   edit b813011 git 작성자 변경 테스트(얘가 잘못되었어)
   pick 10aa749 [포스팅] 이진 탐색 트리
   
   # Rebase 80be237..10aa749 onto 80be237 (2 command(s))
   #
   # Commands:
   # p, pick = use commit
   # r, reword = use commit, but edit the commit message
   # e, edit = use commit, but stop for amending
   # s, squash = use commit, but meld into previous commit
   # f, fixup = like "squash", but discard this commit's log message
   # x, exec = run command (the rest of the line) using shell
   # d, drop = remove commit
   #
   # These lines can be re-ordered; they are executed from top to bottom.
   #
   # If you remove a line here THAT COMMIT WILL BE LOST.
   #
   # However, if you remove everything, the rebase will be aborted.
   #
   # Note that empty commits are commented out
   ```

   이때 수정하고자 하는 commit의 `pick` command를 `edit` 으로 바꿔준다.

   이후 변경 내용을 저장하고 나간다.

   (여러 개의 commit의 내용을 바꿔도 된다) 

4. **작성자(author) 수정하기**

   이제 아래의 명령어로 작성자를 수정한다.

   ```bash
   # email 주소는 반드시 <>로 감싸주어야 한다
   git commit --amend --author="username <email>"
   ```

5. **다음 커밋 수정하기**

   해당 commit에서 수정이 완료되었으면 아래 명령을 통해서 해당 commit의 rebase 작업을 종료한다.

   ```bash
   git rebase --continue
   ```

   만약 수정할 commit이 더 남아있다면 다음 commit을 대상으로 수정이 진행되고,

   만약 더 이상 수정할 commit이 남아있지 않다면 `Successfully reased and updated refs/heads/master` 라는 메세지가 뜬다.

6. **push 하기**

   이후 로컬에 반영한 commit 내용을 원격 저장소로 push한다. 

   다만, rebase 작업 이후에는 `--force` 옵션이나 브랜치 앞에 `+` 를 붙여서 강제로 push해야 한다.

   ```bash
   git push origin +`branch name`
   ```

   

참고자료: [git commit author 변경(커밋 작성자 이름 변경하기)]("https://madplay.github.io/post/change-git-author-name"), [이미 커밋된 내용에서 author(작성자) 수정하기]("https://jojoldu.tistory.com/120") 



