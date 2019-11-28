## Jupyter Notebook

#### Jupyter Notebook에 가상 환경 kernel 추가하기

---

**0. env?**

conda 환경에서 *env* 란 anaconda 내의 독립적인 작업 환경을 의미한다.

쉽게 Python에서의 가상 환경(venv)와 유사하다고 생각하면 된다.



**1. env 생성/삭제/확인**

 1) env 생성

```shell
conda create -n [envName] python=3.6
```

2) env 삭제

```shell
conda env remove -n [envName]
```

3) 생성된 env 목록 확인하기

```shell
conda env list
```

```shell
conda info --envs
```



**2. 가상 환경 kernel 추가하기**

1) 가상환경 활성화

```shell
source activate [envName]
```

2) 가상 환경에 jupyter notebook 설치

```shell
pip install ipykernel
```

3) jupyter notebook에 가상환경 kernel 추가

```shell
python3 -m ipykernel install --user --name [envName] --display-name "[displayKernelName]"
```

이렇게 입력하면 [displayKernelName]이란 이름의 kernel이 추가된다. 이후 jupyter notebook을 실행해서 해당 이름의 kernel이 추가되었는지 확인한다.

4) 가상환경 비활성화

```shell
conda deactivate
```

(macOS 기준)



참고자료: [아나콘다 env 생성, 삭제]("https://blog.naver.com/smilewhj/221369440020?viewType=pc"), [jupyter notebook에 가상환경 kernel 추가하기](https://medium.com/@5eo1ab/jupyter-notebook에-가상환경-kernel-추가하기-ed5261a7e0e6), [Conda activate not working(StackOverflow)]("https://stackoverflow.com/questions/47246350/conda-activate-not-working") 



#### 터미널에서 (base) 가 앞에 계속 붙는 문제

---

가상 환경을 세팅하고 나서, 터미널을 실행할 때마다 앞에 가상 환경처럼 *(base)* 가 붙는 경우가 있다. 이것은 `auto_activate_base` 설정이 변경되었기 때문이다. 먼저 이 설정의 문제인지 확인하기 위해서는 아래의 명령어를 실행해준다.

```shell
conda config --show | grep auto_activate_base
```

만약 위의 명령어의 결과가 참인 경우, 아래 명령어를 실행해준다.

```shell
conda config --set auto_activate_base False
```



참고자료: [Why does '(base)' appear in front of my terminal prompt? (StackExchange)]("https://askubuntu.com/questions/1026383/why-does-base-appear-in-front-of-my-terminal-prompt") 