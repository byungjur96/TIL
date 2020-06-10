# Instance 생성

## GCP로 딥러닝 개발 환경 세팅하기

### 1. 인스턴스 만들기

1. **GCP(Google Cloud Platform) 프로젝트 생성하기**

   GCP 콘솔 안에서 상단에 프로젝트를 선택하여 새 프로젝트를 생성한다.

   ![](https://user-images.githubusercontent.com/29116445/84217382-f6fab380-ab06-11ea-97cf-33de3fba4a4c.png)

2. **Instance 만들기**

   프로젝트를 생성하고 나면 이후 좌측의 메뉴탭을 눌러서 'Compute Engine' 탭의 'VM 인스턴스'를 클릭한다.

   <img src="https://user-images.githubusercontent.com/29116445/84217376-f3ffc300-ab06-11ea-8800-e7f4f8639609.png" style="zoom:50%;" />

   이후 인스턴스 만들기를 클릭하여 새로운 VM 인스턴스를 만든다.

   ![](https://user-images.githubusercontent.com/29116445/84217383-f7934a00-ab06-11ea-93b1-c7ee7e3995d0.png)

   이때 이름을 설정해주고, 예산에 맞게 CPU를 설정해준다.

   만약 GPU를 할당하려면 'CPU 플랫폼 및 GPU'를 선택하고 GPU를 선택해준다.

   하단에 '부팅 디스크'에서 운영체제를 Ubuntu 18.04로 변경해준다.

3. **GPU 할당 받기**

   기본적으로 GCP 내에서 유저가 사용할 수 있는 GPU의 개수는 0개이다. 따라서 신청을 해서 GPU를 할당받아야 한다.

   GCP 좌측 메뉴 버튼을 눌러서 'IAM 및 관리자'의 '할당량'으로 들어간다.

   ![](https://user-images.githubusercontent.com/29116445/84217389-f95d0d80-ab06-11ea-92e2-590535f84e81.png)

   할당량에 들어가서 측정항목을 'GPUs(all regions)'로, 위치를 '글로벌'로 설정한다.

   ![](https://user-images.githubusercontent.com/29116445/84217390-f95d0d80-ab06-11ea-90c7-64eb9e75814f.png)

   ⚠️ 위치를 글로벌로 설정해주지 않은 경우 알 수 없는 에러가 발생했음.

   서비스를 체크해준 후에 위의 '할당량 수정'을 클릭하여 한도를 1로 올려서 신청을 한다.

   ⚠️ 2개 이상을 신청하는 경우 알 수 없는 이유로 거절한다.

   신청을 하고나면 얼마 지나지 않아서 아래와 같은 내용의 메일을 받을 수 있다.

   ![](https://user-images.githubusercontent.com/29116445/84217388-f8c47700-ab06-11ea-975c-a43215ea7454.png)

   이 메일을 받으면 GPU 할당이 완료된 것이며 Instance 생성 후 GPU를 할당해주면 된다.



### 2. ssh를 통한 로컬과 연결

1. **로컬 내에 ssh 키 생성**

   terminal을 통해서 ssh 키를 다음과 같이 생성한다.

   ```bash
   ssh-keygen -t rsa -f <key name> -C "<full email>"
   ```

   위의 방법으로 ssh 키를 생성하면 `<key name>.pub` 이란 파일과 `<key name>` 이란 파일이 생성된다. 이후 `cat` 명령어를 통해서 `.pub` 파일의 키 내용을 확인한다. 확인을 해보면 email로 끝나는 것을 확인할 수 있다. 

2. **VM Instance에 SSH 키 추가**

   ![](https://user-images.githubusercontent.com/29116445/84217385-f82be080-ab06-11ea-8671-d86cceed6a1f.png)

   이후 RSA Key Pair의 내용을 GCP VM Instance의 메타 데이터의 SSH키에 복사한다.

   위의 이미지에서 `수정` 버튼을 누르고 키를 추가하면 된다.

3. **terminal을 통해 접속**

   이후 터미널에서 `ssh -i ~/.ssh/<key name> <USERNAME>@<외부IP>` 를 입력하면 Instance에 접속할 수 있다.





## 기타 오류

### 1. RSA 공유키 충돌 문제

하나의 RSA 공유키로 다른 서버에 접속하려고 하면 아래와 같은 에러 메세지가 출력된다.

```bash
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@ @ WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED! @ @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
```

이런 메세지가 뜨는 이유는 기존에 접속한 적 있는 서버와 RSA 공유키를 교환한 상태에서 해당 서버가 바뀌었기 때문이다. 이 메세지는 '중간자 공격'에 대한 경고를 한다.

이를 해결하기 위해서는 공유키의 IP 정보를 초기화하면 된다.

```bash
ssh-keygen -R <IP name>
```



참고자료: [GCP에서 GPU 할당받고 우분투 가상환경 실행](https://turtlefromocean.tistory.com/3), [생성된 GCP를 SSH로 접속하기](https://ruuci.tistory.com/6), [SSH 접속시 RSA 공유키 충돌 문제 해결]("https://cpuu.postype.com/post/30065"), [GCP error: Quota 'GPUS_ALL_REGIONS' exceeded. Limit: 0.0 globally](https://stackoverflow.com/questions/53415180/gcp-error-quota-gpus-all-regions-exceeded-limit-0-0-globally) 

