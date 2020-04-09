## EC2

### EC2 인스턴스에 SSH로 접속하기 (Mac)

---

1. AWS 관리자 콘솔에서 EC2 콘솔에 접속한다.

2. 상단의 `연결` 을 클릭한다.

   ![](https://github.com/byungjur96/TIL/blob/master/AWS/img/Connect.png)

3. `독립실행형 SSH 클라이언트` 를 클릭해준다.

   ![](https://github.com/byungjur96/TIL/blob/master/AWS/img/SSH.png)

4. 좌측 탭에서 네트워크 및 보안 > 키페어에 들어가서 프라이빗 키를 발급 받는다.

   ![](https://github.com/byungjur96/TIL/blob/master/AWS/img/KeyPair.png)

5. 발급받은 프라이빗 키는 `Users/[유저 이름]/.ssh` 에 저장을 한다. 이때 아래의 `chmod` 명령어로 pem 파일의 권한을 조정한다.

   ```bash
   chmod 400 [프라이빗 키 파일 이름].pem
   ```

6. 이후 아래 명령어를 통해서 EC2 인스턴스에 접속한다.

   ```bash
   ssh -i [프라이빗 키 파일 이름].pem ubuntu@[public DNS]
   ```

   \* 만약 EC2로 ubuntu 가상 머신을 설치했다면 `ec2-use`  말고 `ubuntu` 를 입력해야 한다. 이 부분으로 인해서 오류가 발생할 수 있다.



참고자료: [EC2 인스턴스에 SSH로 접속하기]("https://wingsnote.com/53")



### VSCode에서 SSH로 AWS 연결해서 사용하기

---

1. 다음과 같은 text 파일을 만든다.

   ```
   # Read more about SSH config files: https://linux.die.net/man/5/ssh_config
   Host aws-ec2
       HostName example.com
       User example
       IdentityFile C:\Users\Example\.ssh\aws-example-user.pem
   ```

   `Host` : VSCode에서 나타날 이름

   `HostName`: 서버 IP (Public DNS)

   `User` : Ubuntu username

   `IdentityFile`: 프라이빗 키 경로

2. 위의 text 파일을 `Users/[유저 이름]/.ssh` 에 저장해준다.

3. VSCode에서 'Remote Development'라는 확장팩을 설치한다.

4. 이후 `F1` 키를 누른 다음 'Remote-SSH: Connect to Host..' 를 선택한다

5. 이후 원하는 Host 이름을 선택하면 VSCode에 원격 서버의 파일이 뜨게 된다.



참고자료: [vsCode ssh로 원격서버(AWS) 연결해서 사용하기!]("https://hjson.tistory.com/48"), [Remote Development with Visual Studio Code onAmazon EC2]("https://letswp.io/remote-development-visual-studio-code-amazon-ec2/")

