## [Module] urllib

#### 'module' object has no attribute 'urlopen'

------

```python
import urllib

file = urllib.urlopen(<url_addr>)
s = file.read()
```

위와 같은 코드를 실행하면

> 'module'object has no attribute 'urlopen'

와 같은 에러가 발생한다. 그 이유는 `urlopen()` 메소드는 python 2.x에서 작동하는 메소드이기 때문이다.

Python 3.x를 사용하는 경우에는 아래와 같은 방법으로 url을 연다.

```python
import urllib.request

with urllib.request.urlopen(<url_addr>) as url:
  s = url.read()
```



참고자료: https://stackoverflow.com/questions/3969726/attributeerror-module-object-has-no-attribute-urlopen



#### “SSL: CERTIFICATE_VERIFY_FAILED” Error

---

해당 오류는 `urlopen()` 함수와 `urlretrieve()` method에서 발생했다.

동일한 오류 메세지였지만 해결 방법은 서로 달랐다.

##### 1) `urlopen()`

method 안에 `context` 라는 argument를 추가로 넣어주었다. 이때 `ssl` 라이브러리를 추가로 import하였다.

```python
import ssl
context_value = ssl._create_unverified_context()
```

위의 두 줄을 코드에 추가한 다음, 아래와 같이 `urlopen()` method 안에 context란 argument로 넣어주면 된다.

```python
with urllib.request.urlopen(url, context=context_value) as specific_url:
  specific_page = specific_url.read()
```



##### 2) `urlretrieve()`

`urlopen()` method와 마찬가지로 `context` argument를 추가해주려고 헀는데 존재하지 않는 argument라는 경고가 발생하였다. `urlretrieve()` 의 경우에는 `certifi` 라는 라이브러리를 설치해주었더니 오류가 해결되었다.



참고자료: https://stackoverflow.com/questions/27835619/urllib-and-ssl-certificate-verify-failed-error, https://stackoverflow.com/questions/41691327/ssl-sslerror-ssl-certificate-verify-failed-certificate-verify-failed-ssl-c